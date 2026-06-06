<br />
<p align="center">
  <img src="app/src/main/res/mipmap-xxxhdpi/ic_launcher.png" alt="GoPhoto" width="128" height="128">
  <h2 align="center" style="font-weight: 600">GoPhoto</h2>
  <p align="center">
    <a href="https://github.com/guliacer/GoPhoto/releases/latest"><img src="https://img.shields.io/github/v/release/guliacer/GoPhoto?style=flat-square" alt="Latest release" /></a>
    <a href="https://github.com/guliacer/GoPhoto/stargazers"><img src="https://img.shields.io/github/stars/guliacer/GoPhoto?style=flat-square" alt="GitHub stars" /></a>
    <a href="https://github.com/guliacer/GoPhoto/blob/main/LICENSE"><img src="https://img.shields.io/github/license/guliacer/GoPhoto?style=flat-square" alt="License" /></a>
    <img src="https://img.shields.io/badge/Android-10%2B-3DDC84?style=flat-square" alt="Android 10+" />
    <img src="https://img.shields.io/badge/Kotlin-2.1.20-7F52FF?style=flat-square" alt="Kotlin 2.1.20" />
  </p>
  <p align="center">
    一款面向 Android 的开源照片传输应用，当前聚焦 FTP 接收与 USB 导入。
    <br />
    <a href="https://github.com/guliacer/GoPhoto" target="blank"><strong>GitHub 仓库</strong></a>&nbsp;&nbsp;|&nbsp;&nbsp;
    <a href="https://github.com/guliacer/GoPhoto/releases" target="blank"><strong>下载页面</strong></a>&nbsp;&nbsp;|&nbsp;&nbsp;
    <a href="https://github.com/guliacer/GoPhoto/issues" target="blank"><strong>反馈问题</strong></a>&nbsp;&nbsp;|&nbsp;&nbsp;
    <a href="CONTRIBUTING.md" target="blank"><strong>贡献指南</strong></a>&nbsp;&nbsp;|&nbsp;&nbsp;
    <a href="SECURITY.md" target="blank"><strong>安全策略</strong></a>
  </p>
</p>

![GoPhoto home](gophoto_home_shadow_soft.png)

## 前言

GoPhoto 希望解决相机照片导入安卓手机不够顺手的问题。项目以轻量、直接、可审计为目标，优先把“接收文件、浏览文件、稳定导入、可追踪传输状态”这些基础能力做好。

当前版本主要提供两种使用方式：FTP 接收模式和 USB 模式。它适合需要把相机素材快速转移到手机、现场初筛照片、或在安卓设备上保留一份传输记录的摄影场景。

## 特性

- FTP 接收模式：在手机端启动本地 FTP 接收服务，将传入文件保存到指定目录。
- USB 模式：识别已连接的相机或 USB 存储设备，浏览文件并选择导入。
- 文件浏览：支持常见图片、RAW 和视频文件类型，并提供列表、网格等浏览方式。
- 批量传输：展示当前文件、总进度、速度、剩余时间，并支持暂停、继续、取消与重试。
- 传输记录：保留导入历史，方便回看最近保存的素材。
- 图像压缩：在传输历史中选择图片后，可批量压缩并覆盖保存、新名称保存或导出到压缩目录；交互与批处理思路参考了 Imagine。
- 本地预览：支持图片预览和视频预览，便于导入后快速确认内容。
- 稳定性辅助：包含权限检查、存储空间检查、电池优化提示、连接诊断和日志查看。
- Android 原生体验：使用 Kotlin、Jetpack Compose、Material 3、Hilt、Room、DataStore 构建。

## Todo List

- [x] FTP 接收模式
- [x] USB 文件浏览与导入
- [x] 批量传输进度与任务控制
- [x] 传输历史与本地预览
- [x] 传输历史图像压缩
- [x] 权限检查、日志与诊断入口
- [ ] 发布正式 Release 安装包
- [ ] 完善设备兼容性清单
- [ ] 补充更完整的使用说明与截图

更新日志可查看 [Commits](https://github.com/guliacer/GoPhoto/commits/main/)。

## 安装

### 1. 使用安装包

访问 [Releases](https://github.com/guliacer/GoPhoto/releases) 页面下载最新 APK。如果 Releases 暂无可用安装包，请先使用源码构建。

### 2. 从源码构建

```sh
git clone https://github.com/guliacer/GoPhoto.git
cd GoPhoto
```

使用 Android Studio 打开项目，等待 Gradle 同步完成后运行 `app` 模块。

Windows 命令行构建：

```sh
.\gradlew.bat assembleDebug
```

macOS / Linux 命令行构建：

```sh
./gradlew assembleDebug
```

构建产物通常位于 `app/build/outputs/apk/debug/`。

## 开发

### 环境要求

- Android Studio 最新稳定版
- JDK 17
- Android SDK Platform 36
- Android Gradle Plugin 8.7.3
- Kotlin 2.1.20

### 常用命令

```sh
# 单元测试
.\gradlew.bat testDebugUnitTest

# Debug 构建
.\gradlew.bat assembleDebug

# 连接真机或模拟器后的仪器测试
.\gradlew.bat connectedDebugAndroidTest
```

macOS / Linux 环境将 `.\gradlew.bat` 替换为 `./gradlew`。

### 项目结构

```text
app/src/main/java/com/gophoto/app/
  core/connection/    连接状态、设备检测与诊断
  core/file/          文件浏览、保存、预览与缓存
  core/transfer/      FTP 接收、批量传输、恢复与进度
  core/permission/    Android 权限检查
  core/logging/       应用日志
  data/               Room 数据库实体与 DAO
  ui/screens/         Jetpack Compose 页面
  ui/theme/           主题、色彩、间距、动效
  viewmodel/          页面状态与业务调度
```

## 反馈

欢迎通过 [Issues](https://github.com/guliacer/GoPhoto/issues) 提交问题、兼容性反馈或功能建议。提交问题时请尽量附上 Android 版本、设备型号、连接方式、复现步骤和必要日志。

如果你愿意参与开发，请先阅读 [贡献指南](CONTRIBUTING.md) 与 [贡献者公约](CODE_OF_CONDUCT.md)。

## 免责声明

1. GoPhoto 不是任何相机品牌的官方应用，也不代表任何相机厂商。
2. 本项目用于个人学习、研究与合法的个人素材传输场景。
3. 使用本项目处理的照片、视频和其他素材，其版权和使用责任由使用者自行承担。
4. 请勿在违反当地法律法规、平台规则或设备授权条款的情况下使用本项目。
5. 由于使用、修改或分发本项目导致的数据丢失、设备异常或其他损失，项目维护者不承担责任。

## 致谢

本项目通过 Trae / Codex 等 AI 辅助开发软件构建与迭代，感谢这些工具对项目设计、编码、调试和文档整理提供的帮助。

感谢以下公益 API 与社区资源为开发过程提供支持：

- H站 - 不定时分享免费 key：[https://dc.hhhl.cc/chat/room/amlc1bekzi](https://dc.hhhl.cc/chat/room/amlc1bekzi)
- Codex 公益站 - 每天 60 刀额度：[https://new.sharedchat.cc/list/#/vibe-code/dashboard](https://new.sharedchat.cc/list/#/vibe-code/dashboard)

感谢以下开源项目为本项目提供支持：

- [Imagine](https://github.com/meowtec/Imagine) - 传输历史图像压缩功能的产品参考来源；本项目在 Android 端参考其批量压缩体验与整体工作流，实现了适配 GoPhoto 的 JPEG/PNG/WebP 历史图片压缩，并向 Imagine 提到的 pngquant、mozjpeg、WebP 等图像优化生态致谢。
- [benhoyt/dhash](https://github.com/benhoyt/dhash) - 重复照片检测中轻量 `dHash` 感知哈希路线的参考来源。
- [JohannesBuchner/imagehash](https://github.com/JohannesBuchner/imagehash) - 重复照片检测中 `dHash` 与 `pHash` 多哈希组合思路的参考来源。
- [idealo/imagededup](https://github.com/idealo/imagededup) - 重复图像检索、感知哈希与更重型 ML 方法取舍的工程参考来源。

重复照片检测功能没有直接打包第三方重复检测库，而是在 Android 端参考并改写上述开源项目中常用的感知哈希路线；当前实现使用 `SHA-256` 进行完全重复分组，并结合 `dHash` / `pHash` 做近似重复检测。

## 开源许可

GoPhoto 基于 [GNU General Public License v3.0](LICENSE) 开源。

## 社区文件

- [贡献者公约](CODE_OF_CONDUCT.md)
- [贡献指南](CONTRIBUTING.md)
- [安全策略](SECURITY.md)
- [GPL-3.0 许可证](LICENSE)

## 截图

<p align="center">
  <img src="gophoto_home_shadow_soft.png" alt="Home screen" width="31%" />
  <img src="gophoto_ftp_opt_running.png" alt="FTP receiving screen" width="31%" />
  <img src="gophoto_usb_thumbnail_fixed.png" alt="USB import screen" width="31%" />
</p>
