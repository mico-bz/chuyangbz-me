# chuyangBZ · 个人作品集

**网站：https://chuyangbz.me**

一个用 AI 辅助开发的个人作品展示站，收录 33 个独立项目，其中 6 个可以在浏览器里直接试玩。

## 在线试玩

打开即玩，无需下载安装。

| 项目 | 地址 |
| --- | --- |
| 深渊回廊 · Abyss Corridor | https://chuyangbz.me/games/abyss/ |
| CODE ARENA · 自演化观测台 | https://chuyangbz.me/games/codearena/ |
| 没意思救济所 · 无聊扭蛋机 | https://chuyangbz.me/games/gacha/ |
| 野地 · 开放沙盒 | https://chuyangbz.me/games/openworld/ |
| 山河入镜 · SCENIC WORLD | https://chuyangbz.me/games/scenic/ |
| 废土火线 · WASTELAND FIRELINE | https://chuyangbz.me/games/wasteland/ |

## 内容范围

- **Android 应用**：Kotlin + Jetpack Compose（墨词、喵盒、校园全景制作等）
- **Unity 游戏**：3D 第一人称生存射击、程序化地形与采集建造
- **Three.js / WebGL 网页游戏**：6 个可在线试玩的完整作品
- **桌面工具**：桌面精灵、AI 剪辑引擎、载具工坊
- **AI 创作**：AIGC 短片、概念设定图

## 技术说明

纯静态单页站点，托管在 GitHub Pages，绑定自定义域名 `chuyangbz.me`。

- 无框架、无构建步骤、无外部 CDN 请求
- 所有视觉特效由原生 CSS 与 JavaScript 手写
- 试玩页面使用 Three.js（MIT 协议），许可声明保留在源文件中
- 站点图片：11 张截自本人工程，3 张 AI 生成的概念图已在页面标注
- 未使用任何第三方图片素材、商业字体、模型库或音频文件

## 开发方式

想法先行，拆成能单独跑通的小块，让 AI 写代码、我负责运行和验证，跑不通就一起看日志回到上一步。站点内有一个「一个东西是怎么被做出来的」区块，写的是这套流程。

## 喵盒 MeowBox 发版流程

版本记录与下载页：https://chuyangbz.me/meowbox/

App 内的「检查更新」优先读取 `https://chuyangbz.me/meowbox/update.json`，
读不到才回落到 Appwrite 上的同名单。所以发新版只需要动两个文件：

1. **放 APK**：把新包按 `meowbox/MeowBox-<版本名>-<versionCode>.apk` 命名放进 `meowbox/`。
   文件名里的 versionCode 必须和包里的一致，否则老版本算出来的更新地址会 404。
2. **改清单**：改 `meowbox/update.json` 的 `versionCode`、`versionName`、`apkUrl`，
   把本版改动写进 `notes`（按 `版本号 / 新增 / 改进 / 修复` 分段，App 的更新弹窗原样显示这段文字）。
3. **改页面**：在 `meowbox/index.html` 的版本时间线最上方插入一条本版记录，
   同时更新 `#download` 区块的版本号、文件大小与下载按钮地址。

推上去等 GitHub Pages 构建完即可，App 下次启动就会看到新版。

> 注意：`update.json` 里的 `versionCode` 必须大于用户当前安装的版本，否则 App 判定为已是最新。
> `force` 设为 `true` 时会强制弹窗，`minVersionCode` 用于低于某个版本时静默强制更新。

## 联系

- GitHub：https://github.com/mico-bz
- 邮箱见网站底部
