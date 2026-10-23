# 校园巡检

## 一、项目简介

本项目基于 Kotlin 和 Jetpack Compose 开发，是 Android 实验三的实践项目。在实验二已有工程的基础上，将原有网络测试页面整理为校园巡检页面，并接入 OkHttp 网络请求库，实现 HTTPS 请求与响应结果展示。

本项目主要用于学习 Android 工程结构、页面与网络代码拆分、Gradle 依赖管理以及 Git 版本控制。

## 二、主要功能

1. 展示巡检员姓名、实验室编号和设备巡检数量。
2. 显示设备总数、已检查数量和未检查数量。
3. 支持请求 A203 和 A204 的 HTTPS 回显接口。
4. 展示 HTTP 响应状态码和服务器返回内容。
5. 对网络请求异常进行捕获并显示错误信息。

## 三、技术栈

- Kotlin
- Android SDK
- Jetpack Compose
- Gradle Kotlin DSL
- OkHttp 4.12.0
- Git

## 四、工程结构

项目主要包含以下三个 Kotlin 源码文件：

### 1. MainActivity.kt

应用入口文件，负责创建 Compose 页面、维护请求结果和请求状态，并将网络请求结果更新到页面中。

### 2. InspectionScreen.kt

巡检页面文件，负责展示巡检员、实验室及设备数量信息，提供 A203 和 A204 请求按钮，并计算未检查设备数量。

### 3. InspectionNetwork.kt

网络请求文件，负责创建 OkHttp 客户端、构建 HTTPS 请求、执行网络访问、处理 HTTP 响应以及捕获请求异常。

此外，`app/build.gradle.kts` 用于配置 App 模块的依赖，`AndroidManifest.xml` 用于声明应用权限，`strings.xml` 用于配置应用名称。

## 五、运行方法

1. 使用 Android Studio 打开本项目。
2. 检查 Android SDK 配置，并执行 Gradle Sync。
3. 确认模拟器或 Android 真机可以正常运行，并具备网络访问条件。
4. 使用 Android Studio 运行应用。
5. 在校园巡检页面中点击相应按钮，观察请求结果。

## 六、网络请求说明

本项目使用 OkHttp 访问 HTTPBin 公共回显接口：

- A203：`https://httpbin.org/get?room=A203`
- A204：`https://httpbin.org/get?room=A204`

服务器正常响应时，可通过返回 JSON 中的 `args.room` 字段检查实际请求参数。

实际 HTTP 状态码和响应结果以运行时测试为准。请求成功与否取决于设备网络及服务端状态。

## 七、实验说明

本项目用于验证 Android 工程文件定位、Compose 页面整理、源码职责拆分、第三方网络库接入、HTTPS 请求和 Git 提交流程。

当前实验仅进行公共回显接口测试，不实现真实巡检任务获取或巡检记录持久化。Room、DataStore 和 WorkManager 等内容留待后续实验学习。
