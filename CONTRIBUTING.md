# 贡献指南

感谢你考虑为 Dev Toolbox 做出贡献！

## 开发环境设置

1. 克隆仓库
```bash
git clone https://github.com/yourusername/dev-toolbox.git
cd dev-toolbox
```

2. 安装依赖
```bash
npm install
```

3. 启动开发服务器
```bash
npm run dev
```

## 开发规范

### 代码风格

- 使用 TypeScript 进行开发
- 遵循 ESLint 规则
- 使用有意义的变量和函数命名

### Git 提交规范

使用语义化提交信息：

```
feat: 添加新工具
fix: 修复 Bug
docs: 更新文档
style: 代码格式调整
refactor: 重构代码
test: 添加测试
chore: 构建/工具变更
```

示例：
```
feat: 添加 YAML 格式化工具
fix: 修复 JSON 解析大数字精度问题
docs: 更新 README
```

### 创建新工具

1. 在 `src/components/tools/` 创建工具组件
2. 在 `src/config/tools.tsx` 中注册工具
3. 在 `src/components/layout/tool-content.tsx` 中添加路由
4. 添加相应的国际化文本（如需要）

## Pull Request 流程

1. Fork 本仓库
2. 从 `main` 创建特性分支
3. 进行开发并提交更改
4. 确保代码通过 ESLint 检查
5. 创建 Pull Request

## 问题反馈

如果你发现 Bug 或有新功能建议：

1. 先搜索是否已有相关 Issue
2. 创建新的 Issue 并详细描述问题
3. 对于 Bug，请提供复现步骤

## 许可证

通过贡献代码，你同意你的贡献将按照 MIT 许可证发布。

---

再次感谢你的贡献！ 🎉
