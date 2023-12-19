# JCore-RN

极光 `JCore` SDK 的 `React Native` 封装，支持 `Android` 和 `iOS`，Fork 自 [jcore-react-native](https://github.com/jpush/jcore-react-native)。

----

为啥自己维护一份呢？因为官方 `jcore-react-native` 和`jpush-react-native` 项目做得比较早，各方面更新比较慢。最初我跟着 `jpush-react-native` 文档配置，很多东西没生效，最后去看官方 Android [SDK 集成](https://docs.jiguang.cn/jpush/client/Android/android_guide)和 iOS [SDK 集成](https://docs.jiguang.cn/jpush/client/iOS/ios_guide_new)文档才恍然大悟。

如果有一点 Android 和 iOS 开发经验，建议也去看下官方的[客户端 SDK](https://docs.jiguang.cn/jpush/client/)文档，很多问题在里面都可以找到答案。

有疑问或者本项目存在问题，请在 [Issues](https://github.com/atypiape/jcore-rn/issues) 中反馈，非常感谢。

相关链接：[jpush-rn](https://www.npmjs.com/package/jpush-rn)

## 安装

**NPM:**

```bash
npm i jcore-rn
```

**YARN**

```bash
yarn add jcore-rn
```

## SDK 版本

### Android

`Android` 使用 `mavenCentral` 自动集成 [JCore](https://mvnrepository.com/artifact/cn.jiguang.sdk/jcore) SDK，当前版本为 `4.5.3`。

### iOS

`iOS` 使用 `Cocoapods` 自动导入 [JCore](https://cocoapods.org/pods/JCore) SDK，当前版本为 `4.4.2-noidfa`。

想使用 `idfa` 版本，可以修改自己项目下的 `node_modules/jcore-rn/ios/RCTJCore.podspec`，去掉 `-noidfa`：

```ruby
# 去掉 `-noidfa`
# s.dependency 'JCore', "4.4.2-noidfa"
s.dependency 'JCore', "4.4.2"
```
生成修复补丁：

```bash
npx patch-package jcore-rn
```

接着，在你项目的 `package.json` 中添加 `postinstall` 脚本：

```json
"scripts": {
  "postinstall": "patch-package"
}
```

最后，记得安装 `patch-package`：

**NPM:**

```bash
npm i patch-package -D
```

**YARN:**

```bash
yarn add patch-package -D
```

这样子，以后每次安装依赖时，都会自动打补丁。

