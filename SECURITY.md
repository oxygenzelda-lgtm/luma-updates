# 安全报告 / Security reporting

## 版本范围

请优先检查最新正式版，报告时写明完整版本与构建号。历史版本保留供追溯；本项目目前未承诺旧版长期安全维护或固定响应时限。

## 报告方式

若仓库的 **Security → Report a vulnerability** 入口可用，请通过该入口私下报告。当前仓库尚未公布专用安全邮箱，也未确认该入口已启用；若入口不可用，请先发一个不含漏洞细节的 Issue，请维护者提供私下沟通方式。

公开 Issue 仅用于联系维护者，不应包含可利用的漏洞步骤、攻击文件或敏感日志。私下沟通渠道建立后，再提供影响版本、最小复现、潜在影响和脱敏证据。

## 敏感资料

不要提交真实书库、阅读记录、私人备份、账号密码、Cookie、访问令牌、Android 签名密钥或含密码的配置。测试样本请使用自行编写的少量文本或自制图片。

安装包 SHA256 只能验证文件与发布记录的一致性；依赖公告查询、历史回归测试或可下载状态均不能证明没有漏洞。

## English

Use GitHub's private vulnerability reporting entry if it is available. If it is unavailable, open a minimal issue asking for a private contact channel without disclosing the vulnerability. No dedicated security email or response-time commitment is currently published. Do not post exploit details, private content, credentials or signing keys in public issues.
