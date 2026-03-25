# 部署指南

## 1. CI/CD 流程

```
┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐
│  Push   │───▶│  Build  │───▶│  Test   │───▶│ Deploy  │
│  Code   │    │  App    │    │         │    │         │
└─────────┘    └─────────┘    └─────────┘    └─────────┘
```

## 2. GitHub Actions

### Android CI

```yaml
name: Android CI

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main, develop]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-java@v4
        with:
          distribution: 'temurin'
          java-version: '17'
      - uses: gradle/gradle-build-action@v2
      - run: ./gradlew assembleDebug
      - uses: actions/upload-artifact@v4
        with:
          name: app-debug
          path: app/build/outputs/apk/debug/app-debug.apk
```

### iOS CI

```yaml
name: iOS CI

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main, develop]

jobs:
  build:
    runs-on: macos-latest
    steps:
      - uses: actions/checkout@v4
      - uses: maxim-lobanov/setup-xcode@v1
        with:
          xcode-version: '15.4'
      - run: xcodebuild build -project TangHuApp.xcodeproj -scheme TangHuApp
```

## 3. 环境配置

### 开发环境

- API Base URL: `https://dev-api.tanghu.com`
- 日志级别: DEBUG
- 调试功能: 开启

### 测试环境

- API Base URL: `https://staging-api.tanghu.com`
- 日志级别: INFO
- 调试功能: 部分开启

### 生产环境

- API Base URL: `https://api.tanghu.com`
- 日志级别: ERROR
- 调试功能: 关闭

## 4. 版本管理

### 版本号格式

```
主版本.次版本.修订版本
1.0.0
```

- **主版本**: 重大架构变更
- **次版本**: 新功能迭代
- **修订版本**: Bug修复、小优化
