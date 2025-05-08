# Focus - Mac随机时钟应用

一个简单的macOS专注时钟应用，帮助你提高工作效率。应用会在随机时间点提醒你休息，保护眼睛和身体健康。

## 功能特点

- 专注时钟：默认90分钟工作，20分钟休息
- 随机休息提醒：在设定的时间间隔内，随机提醒你休息
- 系统通知：通过系统通知和声音提醒你休息和工作状态
- 状态栏显示：在菜单栏显示当前计时状态
- 专注统计：记录每日完成的专注次数

## 从GitHub Actions获取最新构建

本项目使用GitHub Actions自动构建。你可以按照以下步骤获取最新的构建版本：

1. 访问本项目的GitHub仓库
2. 点击"Actions"选项卡
3. 在左侧选择"Build Focus App"工作流
4. 点击最新的成功构建
5. 在"Artifacts"部分下载"Focus-app"文件
6. 解压下载的zip文件，获取Focus.app应用程序

## 本地运行与构建

### 运行应用

1. 克隆仓库到本地
   ```bash
   git clone [仓库URL]
   cd Focus
   ```

2. 使用Xcode打开项目
   ```bash
   open Focus.xcodeproj
   ```

3. 在Xcode中点击运行按钮(▶️)即可启动应用

### 本地构建应用

1. 使用Xcode构建
   ```bash
   xcodebuild clean build -project Focus.xcodeproj -scheme Focus -configuration Release -derivedDataPath ./DerivedData
   ```

2. 构建完成后，应用位于以下路径
   ```
   ./DerivedData/Build/Products/Release/Focus.app
   ```

3. 你可以将此应用拖到Applications文件夹中安装

## 注意事项

- 由于使用无签名构建，首次运行可能需要在"系统偏好设置->安全性与隐私"中允许应用运行
- macOS Catalina及以上版本用户可能需要右键点击应用并选择"打开"来绕过Gatekeeper
- 应用会在系统启动时请求通知权限，请允许以获得完整功能体验

## 自定义设置

在应用设置中，你可以自定义：
- 工作时长（默认90分钟）
- 休息时长（默认20分钟）
- 随机提醒最小间隔（默认3分钟）
- 随机提醒最大间隔（默认5分钟）
- 微休息时长（默认10秒）
- 启用/禁用提示音
- 显示/隐藏状态栏图标

## 项目结构与核心文件

本项目主要包含以下核心目录和文件：

- `Focus/`: 应用程序的源代码，包含主要的业务逻辑和UI实现。
  - `FocusApp.swift`: 应用的入口，负责启动和生命周期管理。
  - `ContentView.swift`: 主视图，展示专注计时和控制按钮。
  - `TimerManager.swift`: 计时管理，处理专注/休息倒计时和提示音逻辑。
  - `StatusBarController.swift`: 状态栏控制器，管理菜单栏图标和用户交互。
  - `StatusBarView.swift`: 状态栏视图，展示剩余时间及状态信息。
  - `SettingsView.swift`: 设置界面，用于自定义时间和其他偏好。
  - `VerticallyAlignedTextFieldCell.swift`: 垂直对齐的文本单元格，用于设置界面输入框。
  - `Info.plist`: 应用属性列表，配置 Bundle 标识、权限和版本信息。
  - `Focus.entitlements`: 权限文件，声明 App Sandbox 权限配置。
  - `Assets.xcassets/`: 资源目录，存放图标和图片等资源。
  - `Preview Content/`: SwiftUI 预览资源目录。
- `Focus.xcodeproj/`: Xcode 项目文件，用于配置、构建和管理项目。
- `README.md`: 项目说明文档，包含项目介绍、功能、使用方法等。
- `FocusTests/` 和 `FocusUITests/`: 项目的单元测试和UI测试代码。
- `images/`: 存放项目相关的图片资源。
- `Focus.app.zip`: 构建生成的应用打包文件。
