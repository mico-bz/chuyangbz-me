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

## 喵盒 MeowBox 版本记录页

页面：https://chuyangbz.me/meowbox/

**当前状态：页面不提供下载入口，应用内更新照常。** 页面上的下载按钮已替换为不可点的
「页面不提供下载」标识，页面上没有任何指向 APK 的链接；`update.json` 标记
`"distribution": "unlisted"`，`apkUrl` **保留有效直链**，指向 `meowbox/pkg/` 下
改过名的包（`mb-<versionCode>-<hash>.apk`）。App 的「检查更新」依赖这条直链，不能清空。
页面本身保留，用于公开版本记录、权限清单与免责条款。

> 关于这条链的边界，别抱错预期：本仓库是公开仓库（GitHub Pages 免费版要求公开），
> 所以 `meowbox/pkg/` 下的包在 GitHub 网页上可以直接浏览并下载，`update.json` 也是
> 公开可读、里面有完整 `apkUrl`。换个不容易猜的文件名只降低「顺藤摸瓜」的概率，
> **不构成访问控制**。清 git 历史同样无意义 —— 新旧路径指向的是同一个 blob。
> 真正起作用的是「页面不作为分发渠道」这个定位，不是技术上的不可达。

### 恢复分发时怎么做

App 内的「检查更新」优先读取 `https://chuyangbz.me/meowbox/update.json`，
读不到才回落到 Appwrite 上的同名单。恢复分发要动三处：

1. **放 APK**：把包放进 `meowbox/pkg/`，命名 `mb-<versionCode>-<8位hash>.apk`
   （hash 随便取，作用是让文件名不可猜）。文件名里的 versionCode 必须和包里的一致，
   否则老版本算出来的更新地址会 404。旧的 `meowbox/MeowBox-<版本名>-<versionCode>.apk`
   命名已废弃，别再用。
2. **改清单**：`update.json` 里把 `apkUrl` 更新为新包的完整直链，
   `distribution` 保持或改回 `"unlisted"`（`"public"` 仅在你确实要在页面上挂下载入口时用），
   同时更新 `versionCode`、`versionName`，并把本版改动写进 `notes`
   （按 `版本号 / 新增 / 改进 / 修复` 分段，App 的更新弹窗原样显示这段文字）。
3. **改页面**（仅当你确实要恢复公开下载）：把 `#download` 区块的 `span.dl-btn-off`
   换回 `<a class="dl-btn" href="pkg/mb-<versionCode>-<hash>.apk" download>`，
   去掉 `dl-off` / `dl-btn-off` 两个类，并更新版本号与时间线。
   如果只想保持「页面不提供下载」，跳过这一步 —— 应用内更新与页面无关，不受影响。

> 注意：`update.json` 里的 `versionCode` 必须大于用户当前安装的版本，否则 App 判定为已是最新。
> `force` 设为 `true` 时会强制弹窗，`minVersionCode` 用于低于某个版本时静默强制更新。
> `apkUrl` 留空时 App 端 `parse()` 会返回 null，等同于「没有可用的更新信息」，
> 不会崩、也不会挡启动 —— 但**也就没有更新了**，这正是上次踩的坑（清空后自己也收不到更新）。
> 除非你真的想彻底停掉更新，否则不要清空 `apkUrl`。

## 联系

- GitHub：https://github.com/mico-bz
- 邮箱见网站底部
