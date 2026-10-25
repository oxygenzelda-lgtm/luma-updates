# Luma 阅读器

本地优先、无广告的 Android / Windows 小说与漫画阅读器。

[下载安装包](https://github.com/oxygenzelda-lgtm/luma-updates/releases/latest) · [使用说明](docs/product/READING_GUIDE.zh-CN.md) · [更新记录](docs/releases/HISTORY.md) · [反馈问题](https://github.com/oxygenzelda-lgtm/luma-updates/issues/new/choose)

## 当前状态

最新正式版 **1.25.0（构建 52）**，发布于 2026-10-16。软件可在设置内检查本仓库发布的更新。

**完整应用源码尚未公开，本仓库目前仍是安装包与文档发布仓库。** 正在准备完整源码、许可证、第三方资源声明和独立构建验证；具体缺项见[开源准备清单](docs/OPEN_SOURCE_READINESS.md)。当前不能从此仓库编译 Luma，也不能把公开下载等同于已完成开源。

## 阅读能力

- 本地导入 TXT、Markdown、EPUB、DOCX、ZIP、CBZ，整理书架与阅读状态。
- 小说分页、字号与排版设置；漫画分页、条漫与阅读方向切换。
- 本机保存阅读位置、书签，提供本地备份与恢复功能。
- 按来源实际支持范围搜索、浏览和阅读公开章节；已缓存章节可断网重开。
- 手机触摸操作，以及 Windows 键盘、鼠标与滚轮操作。

格式支持和操作细节见[使用说明](docs/product/READING_GUIDE.zh-CN.md)。来源的搜索结果不代表整部作品可读，章节缓存也不代表已经下载整本。

## 下载与核对

在 [Releases](https://github.com/oxygenzelda-lgtm/luma-updates/releases) 下载 Android ARM64 APK 或 Windows x64 ZIP。旧版本保留用于追溯，不建议把早期调试包作为日常版本。

在 PowerShell 中核对下载文件，例如：

```powershell
Get-FileHash -Algorithm SHA256 -LiteralPath '.\Luma-1.25.0-Android-arm64.apk'
```

将结果与同一 Release 的 `SHA256.txt` 比较；[最新更新清单](latest/luma-update.json)还列出文件大小与摘要。[历史文件索引](docs/releases/版本文件索引.csv)和[历史校验摘要](SHA256SUMS.txt)用于追溯。这些摘要检查文件是否一致，不代替安装与安全测试。

## 已知限制

- 部分番茄作品可搜索，但目录仍可能加载失败；特殊字体相关复制、文本搜索和下载有限制。
- 在线内容受来源公开范围、网络和站点变化影响，不承诺所有来源或作品都可读。
- 1.25.0 发布记录报告了自动回归与 Android 模拟器检查；实体手机、Windows 原生 UI 和持续性能仍有待验收项。这些历史记录未在本次文档整理中重新执行。
- 历史交接记录中的“当前正式版”“源码不公开”等表述按记录日期理解；当前状态以本节及最新 Release 为准。

## 参与项目

欢迎提交可复现的问题、文档修正和改进建议，见[贡献指南](CONTRIBUTING.md)。安全问题请先阅读[安全报告说明](SECURITY.md)。不要上传私人书籍、阅读记录、备份、账号凭据或签名文件。

## English

Luma is a local-first, ad-free novel and comic reader for Android and Windows. This repository currently distributes release binaries and selected documentation. **The application source code and its open-source license have not been published yet; the app cannot currently be built from this repository.** See the [source-release checklist](docs/OPEN_SOURCE_READINESS.md) for the remaining work. No adoption or build reproducibility claim is made by this documentation update.
