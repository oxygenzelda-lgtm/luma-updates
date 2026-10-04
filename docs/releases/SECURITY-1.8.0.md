# Luma 1.8.0 security review

## 中文审查摘要

本次审查覆盖书源导入与解析、发现页缓存与偏好、网络请求和下载、EPUB/DOCX/漫画压缩包，以及两端更新校验和安装准备。通过静态检查、恶意输入回归与真实联网验证发现并修复了以下边界问题：

- **书源访问内网**：拦截本机、内网、保留地址和混淆IP，直连时验证DNS全部结果并固定实际连接地址；每次重定向重新验证。用户系统主动配置的代理负责它自己的上游DNS。
- **规则伪装与解析膨胀**：导入文件不能冒充内置适配器；限制规则长度、深度、节点展开和提取文本大小，不执行第三方JavaScript。
- **请求和缓存膨胀**：限制响应容量及总时长，每批搜索最多3个工作线程；目录刷新有调度时限。收藏最多300项、目录缓存120项、偏好100条、联想8条，序列化数据最多2 MiB。
- **压缩包膨胀**：对实际解压输出限量，不只相信ZIP填写的大小；保留路径穿越、重复文件、符号链接、成员数及总量保护。纯文本文件限制64 MiB。
- **更新链路**：保留下载大小及SHA256校验、Android包名/版本/原证书核对，以及Windows安全暂存和旧目录回退。Windows依赖可信的发布仓库，SHA256不是独立的发布者签名。

142项全套回归通过；另外3项截图采集通过、21张组件截图检查完成。18个目录联网可用，4个目录在首次超时后重试通过，不能据此保证外站永远可用。中文文库篇目、日文EPUB、西班牙语漫画均实际下载解析通过。发现推荐和阅读偏好保存在本机，没有添加云端画像服务。

本报告不构成“无漏洞”保证，也不能从测试数量推算全软件bug率。原生编解码器、Flutter/Dart及依赖仍需持续维护。没有连接Android设备；真实输入法、持续帧率、设备内存压力和系统升级安装仍待两端实机验收，不能把下载校验通过当作安装成功。

## Detailed audit

Scope: source import/store/parser; discovery metadata, history and favorites; outbound requests, redirects and downloads; local EPUB/DOCX/CBZ imports; update manifests, SHA256, Windows staging and Android installation identity. Static review plus hostile-input regression and live endpoint checks. No penetration-test certification or universal bug-rate claim.

| Finding | Before | Resolution / verification |
| --- | --- | --- |
| Untrusted source could target internal services | HTTPS and userinfo checks alone accepted internal IPs and DNS destinations | Reject loopback/private/reserved IPv4 and IPv6, mapped IPs, local hostnames and numeric disguises; check all DNS results and pass the approved IP directly to Socket.startConnect. Validate every redirect. Tests cover literal targets, mixed forms, DNS-to-private and private redirect. |
| Imported flags could impersonate a built-in adapter | Imported JSON retained lumaBuiltIn/lumaProvider | Strip imported privileged flags. Restore shipped definitions only by known source identity, preserving enable preferences. Malformed rule values remain incompatible; never run JavaScript or decryption code. |
| Rules could expand parser work or create long-running searches | Selector nesting and search session duration not bounded | Cap selector length/layers/intermediate nodes; at most three search workers; session scheduling deadline, bounded response bytes and total request timeout. Generation checks suppress stale results. |
| ZIP metadata did not guarantee actual decoded size | Text archive members readBytes could allocate without enforcing the output limit | Stream to bounded memory for text and bounded files for update members/images; actual output cannot exceed declared member size or the existing per-entry limit. Tests cover output writes/back-references, traversal and complete app staging. |
| Discovery metadata could grow with use | New local feature required explicit limits | Up to 300 online favorites, 120 cached hits, 100 local interests, 8 suggestions; 2 MiB serialized budget, bounded title/author/intro. Serialized writes and atomic replacement. A broken discovery cache does not block the library. |

Existing safeguards verified: local ZIP paths reject absolute/drive/parent traversal, duplicates and symlinks; entry count/per-entry/total output budgets. Remote books have chapter/page/content limits and cancellation; incomplete downloads never enter the saved library. HTML is parsed as data and never rendered in a scripting browser. Update metadata has schema/size/hash validation; both package download and pre-install paths verify SHA256. Android installer checks package name, current signing certificate and newer version. Windows staging validates paths and app files, bounds decoded output, and replacement helper validates sibling paths and retains rollback.

Permissions: Android INTERNET for explicit sources/updates and REQUEST_INSTALL_PACKAGES for user-invoked upgrades. FileProvider is not exported and grants a temporary installation URI. No new contacts/location/microphone permissions or hosted recommendation telemetry added.

Trust and limits: package SHA256 verifies bytes against the trusted configured repository, not a separate cryptographic publisher signature. Android also verifies the existing certificate; Windows updater trusts the configured release repository. An explicitly configured host proxy handles upstream DNS itself; direct socket pinning applies to direct connections. Third-party native image codecs, Flutter/Dart runtime and archive/parser dependencies remain part of the trusted runtime; these tests cannot prove absence of vulnerabilities. Very large plain text now has a 64 MiB limit, preserving normal large novels while preventing a 512 MiB text allocation.

Primary references: [OWASP SSRF prevention](https://cheatsheetseries.owasp.org/cheatsheets/Server_Side_Request_Forgery_Prevention_Cheat_Sheet.html), [Dart connectionFactory](https://api.dart.dev/dart-io/HttpClient/connectionFactory.html), [Dart cancellable socket connection](https://api.dart.dev/dart-io/Socket/startConnect.html), [Gutendex catalog contract](https://gutendex.com/). Implementation is Luma-authored; no executable third-party rule bundle copied.

Native installation, device memory pressure, real keyboard/IME behavior and sustained animation performance need Android/Windows native acceptance. No Android device was connected during this run. Test results and exact published assets are recorded separately; failed exploratory runs are retained and are not described as passing.
