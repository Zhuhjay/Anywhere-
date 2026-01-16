# Anywhere-

::: Tip
该文档内容由 AI 进行生成，需要自行辨别内容真实性
:::


一个强大的 Android 快捷方式管理器，将你常用的页面收集到一个界面，一键直达。

简洁快速无广告、无后台，点击进入 App 即可看到全部快捷方式，轻点一下即可跳转。

优雅美观遵循 Material Design，界面统一不凌乱，永远保持干净。



## 工作模式

Anywhere- 目前支持 3 种工作模式，满足不同需求：

### 1. Normal 模式（推荐）
无需任何运行时权限，通过 **URL Scheme 协议**打开特定页面，也可以通过 **Intent** 打开 Exported 页面。

**适用场景**：
- 支付宝小程序（蚂蚁森林、电影票、火车票）
- 网易云歌单
- 微博热搜
- 酷安动态

**优点**：无需任何运行时权限，可打开指定界面
**缺点**：需要应用支持；不支持所有页面

**添加方式**：
1. 点击主界面右下角的 **+** 号图标
2. 第一项是别名，可以随意填写
3. 第二项是 URL Scheme 链接，可在「捷径社区」中查找或搜索引擎搜索
4. 第三项是描述，选填
5. 点击完成

### 2. Root 模式
通过使用 **ADB 指令**打开指定的页面 (Activity)。

**适用场景**：捷径社区中没有的页面，与 URL Scheme 模式互补
- 主界面 (MainActivity)，或许可以帮助跳过广告页
- 个人信息页（可能需要传递 Intent Extras）
- 更多页面

**优点**：可以打开任何 Activity 页面
**缺点**：暂时不支持打开 Fragment

**添加方式**：
1. 点击右上角齿轮图标进入设置，选择工作模式为 **Root**
2. 点击主界面右下角的 **+** 号图标，请求 Root 权限
3. 获得 Root 权限后程序返回桌面并开启可移动的悬浮窗 ✓ (Collector)
4. 进入想要快速打开的页面，点击悬浮窗，返回程序
5. 第一项是别名，第二项是包名，第三项是类名，第四项是描述
6. 点击完成

::: tip 提示
MIUI 等 ROM 可能需要授权**后台弹出权限**以正常使用此功能。
:::

::: warning 注意
有些应用在**广告加载页/闪屏页**会做一些初始化工作，跳过闪屏页可能导致应用出现问题。
:::

### 3. Shizuku 模式
通过使用 [Shizuku Manager](https://www.coolapk.com/apk/moe.shizuku.privileged.api) 实现无需授予本程序 Root 权限，获得与 Root 模式相同的功能。

**适用场景**：同 Root 模式

**优点**：无需授予 Root 权限实现 Root 模式功能
**缺点**：需要额外下载 Shizuku Manager，Shizuku 需要 Root 模式激活

**添加方式**：同 Root 模式

::: tip 提示
无需 Root 权限不代表手机可以不具有 Root 权限，因打开 Activity 的 adb 指令需要 Root 权限。Shizuku 模式只是让本程序可以不获取 Root 权限，从而保证安全、提高性能并且便于管理。
:::

## 核心功能

### 10种卡片类型

| 类型 | 功能 |
|------|------|
| **URL Scheme** | 通过 URL Scheme 启动应用功能 |
| **Activity** | 直接启动任何 Activity（支持 Extras 参数） |
| **小程序** | 启动支付宝/微信小程序 |
| **二维码** | 扫描并保存二维码快速访问 |
| **图片** | 保存图片作为快捷入口 |
| **Shell** | 执行 Shell 命令（支持 Root/ADB） |
| **开关 Shell** | 切换型命令开关（如免流开关） |
| **文件** | 快速打开文件 |
| **广播** | 发送广播 Intent |
| **工作流** | 执行多个卡片动作的自动化流程 |
| **无障碍** | 模拟点击操作跳转页面 |

### Intent Extras 支持
Activity 和广播卡片支持添加多种类型的 Extras 参数：

```bash
-e|--es <EXTRA_KEY> <EXTRA_STRING_VALUE>          # String
--ez <EXTRA_KEY> <EXTRA_BOOLEAN_VALUE>            # Boolean
--ei <EXTRA_KEY> <EXTRA_INT_VALUE>                # Integer
--el <EXTRA_KEY> <EXTRA_LONG_VALUE>               # Long
--ef <EXTRA_KEY> <EXTRA_FLOAT_VALUE>              # Float
--eu <EXTRA_KEY> <EXTRA_URI_VALUE>                # URI
--ecn <EXTRA_KEY> <EXTRA_COMPONENT_NAME_VALUE>     # Component Name
--eia <EXTRA_KEY> <EXTRA_INT_VALUE>[,...]          # Integer Array
--ela <EXTRA_KEY> <EXTRA_LONG_VALUE>[,...]         # Long Array
--efa <EXTRA_KEY> <EXTRA_FLOAT_VALUE>[,...]        # Float Array
```

例如：
```bash
--es name absinthe
--ei id 123
```

### 特色功能

- **悬浮窗收集器 (Collector)**：快速收集当前屏幕的 Activity/URL Scheme
- **云端规则**：浏览和使用社区共享的卡片规则，支持搜索
- **扫码合集**：内置微信、支付宝、QQ 等扫码快捷方式
  - 微信付款码（无需权限）
  - 支付宝扫码/付款码
  - QQ 扫码
- **WebDAV 备份**：自动备份配置到云端（支持坚果云等）
- **桌面快捷方式**：将卡片添加到桌面
- **快速设置磁贴**：从系统下拉菜单直接启动（最多 7 个），支持自定义图标
- **桌面小部件**：在桌面显示常用卡片
- **分页模式**：支持多页分类管理，左右滑动切换
- **多种布局**：普通/极小/流式布局可选
- **暗黑模式**：Material 3 设计，支持自定义主题

## 添加方式

### 方式一：URL Scheme
通过 URL Scheme 协议快速添加，支持动态参数输入。

### 方式二：活动列表
1. 点击 FAB 按钮 → 选择「应用列表」
2. 选择目标应用（右上角菜单提供显示/隐藏系统应用）
3. 在二级页面中选择 Activity
4. Exported Activity 会显示强调底色
5. 配置参数后保存为卡片

::: warning 注意
已停用或被冻结的 App 无法获取活动列表，请先启用或解冻。
:::

### 方式三：扫码合集
整理扫码合集，里面有微信、支付宝、QQ 等扫码快捷方式：
- 进入扫码合集页面，点击卡片即可打开
- **长按**卡片进行添加
- 此页面的卡片不同于其它启动方式，它是主动适配的，所以不支持显示详细参数

### 方式四：Collector（悬浮窗收集器）
1. 点击主界面 FAB 按钮 → 选择「收集器」
2. 系统会回到桌面，并开启一个对号样式的悬浮窗
3. 进入想要添加的页面，点击对号
4. 自动收集当前页面的 URL Scheme 或 Activity 信息
5. 确认保存为卡片

::: warning 注意
正常地使用此功能需要**悬浮窗**权限，MIUI 等 ROM 可能需要**后台弹出界面**权限。
:::

::: warning 注意
并非所有**当前显示**的页面都可以添加。有些页面是 Fragment、H5、Hybrid 等等，这些技术制作的页面都是不支持快速打开的。
:::

### 方式五：云端规则
1. 点击 FAB 按钮 → 选择「云端规则」
2. 浏览社区共享的卡片规则
3. 支持搜索功能
4. 一键导入使用

### 方式六：高级卡片
1. 点击 FAB 按钮 → 选择「高级选择」
2. 从 11 种卡片类型中选择
3. 填写参数和配置

### 方式七：其他应用分享
分享文本到 Anywhere- 应用，自动识别并创建卡片。
- 此功能只响应**纯文本**分享内容
- Anywhere- 会使用正则表达式提取分享内容中的 URL 并去除多余查询参数

### 方式八：URL Scheme 协议调用
- 复制带有 `anywhere://` 协议的链接自动识别
- 浏览器访问 `anywhere://url?...` 直接添加卡片

## 快速启动

### 桌面快捷方式
1. 长按卡片 → 选择「创建快捷方式」
2. 在桌面任意位置粘贴
3. 直接点击快捷方式启动

### 快速设置磁贴
1. 长按卡片 → 选择「创建磁贴」
2. 在系统下拉菜单中显示
3. 点击磁贴直接启动
4. 支持自定义图标（点击磁贴设置页卡片图标进行设置）

### 桌面小部件
1. 长按桌面空白处 → 小部件 → Anywhere-
2. 选择要显示的卡片
3. 点击小部件启动卡片

### 其他应用 Shortcuts
支持启动其他应用的 Shortcuts，提供更多快捷方式选项。

## 备份与恢复

Anywhere- 提供完整的备份与恢复功能，在「设置 - 备份和恢复」页面操作。

### 1. 备份和分享

**1.1 创建备份**
通过 Document API，Anywhere- 无需读写权限即可完成备份。点击「创建新的备份文件」即可打开文档程序，选择保存位置，备份所有卡片。

**1.2 分享配置**
点击「分享配置」选项，Anywhere- 会生成一串加密数据。此数据包含所有卡片配置，将其复制后即可分享给其他人。

::: warning 注意
**图片卡片**和**文件卡片**不会被备份。
:::

**1.3 云备份**
Anywhere- 支持使用 WebDAV 协议备份数据。以坚果云为例：
- WebDAV 域名：`https://dav.jianguoyun.com/dav/`（必须以 `/` 结尾）
- WebDAV 用户名：填写你的用户名
- WebDAV 密码：根据服务提供商要求填写（坚果云需在设置中申请应用密码）

当数据填写正确后，点击「立即备份」即可触发备份。也可开启「自动备份」，应用将在卡片有改动时自动备份数据。

### 2. 恢复和应用

**2.1 恢复备份**
点击「从存储文件中恢复」选项即可打开文档程序，选择备份的 `*.awbackups` 文件，提示备份成功后即恢复完成。

**2.2 应用配置**
点击「应用配置」选项，粘贴其他人分享的数据串，点击「确定」，即可应用配置。

## 实验室功能

- **透明图标**：规避某些系统生成桌面快捷方式时生成角标
- **解冻应用时提示**：多种方式打开冻结的卡片
- **自动检测规则**
- **启动卡片后关闭 Anywhere-**：启动卡片后自动关闭应用
- **使用废弃方法创建快捷方式**：可能解决快捷方式图标不能填满的问题

## 项目结构

```
Anywhere-/
├── app/                    # 主应用模块
│   ├── src/main/
│   │   ├── java/com/absinthe/anywhere_/
│   │   │   ├── ui/         # 界面层（Activity/Fragment）
│   │   │   ├── adapter/    # RecyclerView 适配器
│   │   │   ├── database/   # Room 数据库
│   │   │   ├── model/      # 数据模型
│   │   │   ├── services/   # 后台服务
│   │   │   ├── utils/      # 工具类
│   │   │   ├── view/       # 自定义视图
│   │   │   └── viewmodel/  # ViewModel
│   │   └── cpp/           # 原生 C++ 代码
│   └── build.gradle.kts
├── color-picker/           # 颜色选择器库模块
└── build.gradle.kts        # 项目级构建配置
```

## 技术栈

- **语言**：Kotlin
- **架构**：MVVM + Repository
- **UI**：Material 3, ViewBinding
- **数据库**：Room 2.5.2
- **异步**：Kotlin Coroutines
- **权限**：Shizuku 12.2.0, libsu 5.2.1
- **网络**：OkHttp 4.11.0, Retrofit 2.9.0
- **图片**：Glide 4.16.0
- **存储**：MMKV 1.3.1
- **响应式**：RxJava 2.x

## 版本信息

- **当前版本**：2.5.5
- **最低系统**：Android 6.0 (API 23)
- **目标系统**：Android 13 (API 33)
- **编译系统**：Android 14 (API 34)

## 权限说明

- `SYSTEM_ALERT_WINDOW`：悬浮窗收集器功能
- `INTERNET`：云端规则和 WebDAV 备份
- `VIBRATE`：触觉反馈
- `POST_NOTIFICATIONS`：通知权限

## 相关链接

- [官方文档](https://absinthe.life/Anywhere-Docs/guide/)
- [文档仓库](https://github.com/zhaobozhen/Anywhere-Docs)
- [GitHub Releases](https://github.com/zhaobozhen/Anywhere-/releases)
- [Google Play](https://play.google.com/store/apps/details?id=com.absinthe.anywhere_)
- [CoolApK](https://www.coolapk.com/apk/com.absinthe.anywhere_)
- [常用 URL Scheme 汇总](https://dodoo.co/prepare/protocol)
- [捷径社区](https://sharecuts.cn/apps)

## 许可证

[GNU General Public License v3.0](LICENSE)
