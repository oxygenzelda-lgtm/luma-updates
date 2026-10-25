# Luma 完整开源准备清单

核查日期：2026-10-25。此文件记录实际状态，不代表完整开源已经完成。

## 已确认的项目

- 仓库：`oxygenzelda-lgtm/luma-updates`，公开可访问。
- 最新发布：1.25.0，构建号 52，2026-10-16。
- 本次 GitHub 查询返回 48 个公开 Release；安装包发布历史不等同于使用人数。
- 现有仓库含更新清单、历史文件索引、校验摘要、使用说明和发布记录。
- 完整应用源码未在默认分支或 Release 附件中找到；维护者说明原始工程在另一台电脑。
- 当前没有应用开源许可证，不能从此仓库独立构建应用。

## 待完成

- [ ] 从原电脑取得与正式版本对应的完整工程，记录版本与提交信息。
- [ ] 核对工程内全部适用的开发说明，先做完整测试与构建基线，再决定具体代码修复。
- [ ] 导入应用源码、Android/Windows 工程、依赖锁文件、必要构建脚本及可公开测试。
- [ ] 清点字体、图标、图片、规则和第三方代码的来源与授权；保留原有许可证和署名，替换无法公开分发的资源。
- [ ] 排除私人书库、正文、封面缓存、阅读记录、原始诊断、账号配置及签名秘密；对拟发布文件和拟推送历史分别检查。
- [ ] 为有权授权的原创代码添加明确的开源许可证，单独列出第三方资源的许可。许可证选择须与实际依赖及授权兼容，不能用仓库许可覆盖第三方内容。
- [ ] 写明真实 Flutter/Dart/原生工具版本、依赖获取、开发启动、测试与双端构建步骤。
- [ ] 在独立目录从公开源码执行静态检查、测试及 Android/Windows 构建；记录哪些实机行为尚未验证。
- [ ] 配置自动检查、依赖更新和私下安全报告入口，并实际验证工作流。
- [ ] 经验证后公开源码，并在 README 明确源码版本与安装包的对应关系；保留既有更新地址及历史发布。

## 工程交接建议

从原电脑提供完整工程压缩包，或推送到当前账号可访问的私有仓库。不要仅复制 `lib/`：还需要原生平台目录、`pubspec.yaml`、`pubspec.lock`、测试、必要资源和构建配置。`build/`、`.dart_tool/` 等生成缓存通常无需交接。

签名密钥、含密码的 `key.properties`、令牌、私人书库和阅读记录应留在原电脑；只提供无秘密的配置样例。若要带入 Git 历史，需先检查历史是否包含已删除的秘密，不能只检查当前工作目录。提供工程后再选择具体开源许可证，当前不以一个空许可证文件宣称应用已开源。

## OpenAI 申请准备

官方入口：[Codex for Open Source](https://developers.openai.com/community/codex-for-oss)，[申请表](https://openai.com/form/codex-for-oss/)。官方说明审核会考虑项目使用情况、生态价值、持续维护和维护者身份；六个月 ChatGPT Pro（含 Codex）由审核决定。

申请前应公开完整可审核工程及许可证。维护者应如实说明项目阶段和自己的职责；没有核实的用户数、下载量、星标、贡献者数、测试结果与生态影响不得编造。发布次数和历史测试记录可以作为有日期的维护材料，不能替代真实采用情况。

本次未提交申请，也未同意申请条款。姓名、ChatGPT 账号邮箱及需要时的 OpenAI Organization ID 应由申请人提供，不能从其他账号信息推定。

## English status

The application is not yet fully open source. The original project is on the maintainer's other computer. The release repository alone is insufficient for source auditing, independent builds or a complete licensing review. Source import, third-party license inventory, secret removal, reproducible build instructions and fresh verification remain pending. Historical release and test records are maintenance evidence only, not evidence of adoption or approval for the OpenAI program.
