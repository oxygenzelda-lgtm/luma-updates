# Luma

本地、无广告的小说、轻小说与漫画阅读器，支持 Android 与 Windows。

- [下载安装包](https://github.com/oxygenzelda-lgtm/luma-updates/releases/latest)
- [完整版本记录](docs/releases/HISTORY.md)
- [新聊天接续文档](docs/releases/HANDOFF.md)
- [安装包表格](docs/releases/版本文件索引.csv)
- [机器可读校验索引](docs/releases/history-manifest.json)

留存18个版本、34份不同安装包，从1.0.0到1.7.0。没有找到0.01安装包。
历史日期来自开发记录，上传日期是本次归档日期；不倒填编译时间。
同一早期版本的r后缀仅用于区分不同字节，不代表时间顺序。

此仓库用于安装包及项目文档分发。Luma完整源码尚未在此公开，源码许可证尚未选定。
发布说明中的evidence/lib/docs路径指本地开发工作区，不代表完整源码已上传。
没有上传个人小说、阅读记录、聊天原文、设备标识、签名私钥或凭据。

## 更新

在Luma的 设置 → 关于Luma → 检查更新 → 更新来源 中填写本仓库地址。
更新清单：[luma-update.json](https://github.com/oxygenzelda-lgtm/luma-updates/releases/latest/download/luma-update.json)。
应用校验附件大小与SHA256；Android升级保持同一包名与签名并由系统确认安装。
Windows包解压后运行luma_validation.exe，更新过程保留旧程序目录。
云端附件发布校验与实际设备上的完整更新安装验收是两个独立步骤；后者仍待完成。

历史Android版本通常不能直接覆盖降级；旧Windows包请解压到独立目录。
首次开发版含自制验证样本和调试包，详情见对应Release；正式1.6.0起移除分发测试样本。
