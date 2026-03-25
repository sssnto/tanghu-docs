# 开发规范

## 1. 代码规范

### Kotlin (Android)

- 遵循 [Kotlin Coding Conventions](https://kotlinlang.org/docs/coding-conventions.html)
- 使用 4 空格缩进
- 文件编码: UTF-8
- 每行不超过 120 字符

### Swift (iOS)

- 遵循 [Swift API Design Guidelines](https://www.swift.org/documentation/api-design-guidelines/)
- 使用 Xcode 默认格式设置
- 文件编码: UTF-8

## 2. Git 流程

### 分支命名

```
feature/[功能名]          # 新功能
bugfix/[问题描述]         # Bug修复
hotfix/[紧急修复]         # 紧急修复
refactor/[重构内容]        # 代码重构
```

### 提交信息格式

```
<type>: <subject>

<body>

<footer>
```

**Type:**
- `feat`: 新功能
- `fix`: Bug修复
- `docs`: 文档更新
- `style`: 代码格式（不影响功能）
- `refactor`: 重构
- `test`: 测试
- `chore`: 构建/工具

### 示例

```
feat: 添加血糖记录功能

- 添加血糖值输入表单
- 支持选择测量类型
- 保存到本地数据库

Closes #123
```

## 3. Pull Request 规范

### PR 创建流程

1. 从 `develop` 分支创建新分支
2. 完成开发并自测
3. 提交 PR 并指定 Reviewers
4. 至少 1 人 Review 通过后合并
5. 删除源分支

### PR 模板

```markdown
## 概述
<!-- 简要描述本次变更 -->

## 变更类型
- [ ] 新功能
- [ ] Bug 修复
- [ ] 重构
- [ ] 文档更新

## 测试情况
<!-- 描述测试情况 -->
- [ ] 本地测试通过
- [ ] 单元测试通过
- [ ] 界面测试通过

## 截图/录屏
<!-- 如有 UI 变更，附上截图 -->

## 相关 Issue
<!-- 关联的 Issue 编号 -->
```

## 4. 代码审查清单

- [ ] 代码符合规范
- [ ] 有适当的单元测试
- [ ] 没有硬编码值
- [ ] 错误处理完善
- [ ] 性能考虑周全
- [ ] 文档已更新（如需要）
