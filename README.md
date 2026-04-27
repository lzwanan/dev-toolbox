# 程序员工具箱 (Dev Toolbox)

<div align="center">

[![License](https://img.shields.io/github/license/lzwanan/dev-toolbox)](https://github.com/lzwanan/dev-toolbox/blob/main/LICENSE)
[![Node.js Version](https://img.shields.io/badge/node-%3E%3D18.0.0-brightgreen)](https://nodejs.org/)
[![React](https://img.shields.io/badge/react-18.x-blue)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/typescript-5.x-blue)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/tailwindcss-3.x-blue)](https://tailwindcss.com/)

一个简洁优雅的在线程序员工具箱，提供常用开发工具、运维工具和趣味测试。

[English](./README_EN.md) | 简体中文

</div>

---

## ✨ 特性

### 🛠️ 开发工具
- **JSON 格式化** - 格式化、校验、压缩、排序
- **YAML 格式化** - YAML 内容格式化
- **Base64 编解码** - Base64 编码和解码
- **URL 编解码** - URL 编码和解码
- **正则表达式测试** - 实时测试正则表达式
- **JWT 解码** - 解码和查看 JWT 内容
- **颜色转换** - HEX/RGB/HSL 颜色格式互转

### ⚙️ 运维工具
- **进制转换** - 二进制、八进制、十进制、十六进制互转
- **时间戳转换** - Unix 时间戳和日期互转
- **Hash 计算** - MD5、SHA1、SHA256、SHA512 哈希计算
- **Cron 表达式** - Cron 表达式生成和解析

### 🎯 实用工具
- **UUID 生成** - 生成 UUID/GUID
- **密码生成** - 生成随机安全密码
- **二维码生成** - 生成二维码

### 🎮 趣味工具
- **MBTI 测试** - 16型人格测试（32/93/144题三种模式）
- **随机决策** - 帮助做随机选择

### 🎨 界面特性
- 🌙/☀️ **暗色/亮色模式** - 支持主题切换
- 📱 **响应式设计** - 适配各种屏幕尺寸
- ⚡ **快速响应** - 基于 Vite 的极速开发体验

---

## 🚀 快速开始

### 环境要求

- Node.js >= 18.0.0
- npm >= 9.0.0 或 yarn >= 1.22.0

### 安装

```bash
# 克隆项目
git clone https://github.com/lzwanan/dev-toolbox.git
cd dev-toolbox

# 安装依赖
npm install

# 启动开发服务器
npm run dev
```

访问 http://localhost:5173 查看效果。

### 构建生产版本

```bash
npm run build
```

构建产物将输出到 `dist` 目录。

---

## 🐳 Docker 部署

### 使用 Docker Compose（推荐）

```bash
# 构建并启动
docker-compose up -d

# 查看状态
docker-compose ps

# 查看日志
docker-compose logs -f

# 停止服务
docker-compose down
```

访问 http://localhost:3000

### 使用 Docker

```bash
# 构建镜像
docker build -t dev-toolbox .

# 运行容器
docker run -d \
  --name dev-toolbox \
  -p 3000:80 \
  --restart unless-stopped \
  dev-toolbox
```

### 群晖 (Synology NAS) 部署

详细部署指南请参考 [DEPLOY.md](./DEPLOY.md)

---

## 📁 项目结构

```
dev-toolbox/
├── src/
│   ├── components/
│   │   ├── layout/           # 布局组件
│   │   │   ├── header.tsx    # 头部
│   │   │   ├── sidebar.tsx   # 侧边栏
│   │   │   ├── main-layout.tsx
│   │   │   └── tool-content.tsx
│   │   ├── providers/         # Provider 组件
│   │   │   └── theme-provider.tsx
│   │   ├── tools/           # 工具组件
│   │   │   ├── json-formatter.tsx
│   │   │   ├── yaml-formatter.tsx
│   │   │   ├── base64-coder.tsx
│   │   │   └── ...
│   │   └── ui/              # UI 基础组件
│   │       ├── button.tsx
│   │       ├── card.tsx
│   │       ├── input.tsx
│   │       └── ...
│   ├── config/
│   │   ├── tools.tsx         # 工具配置
│   │   └── mbti-data.ts     # MBTI 测试数据
│   ├── hooks/
│   │   └── useTheme.tsx     # 主题 Hook
│   ├── lib/
│   │   └── utils.ts         # 工具函数
│   ├── App.tsx
│   ├── main.tsx
│   └── index.css
├── public/
├── docker-compose.yml
├── Dockerfile
├── nginx.conf
└── package.json
```

---

## 🛠️ 技术栈

| 技术 | 说明 | 版本 |
|------|------|------|
| React | UI 框架 | 18.x |
| TypeScript | 类型系统 | 5.x |
| Vite | 构建工具 | 8.x |
| Tailwind CSS | CSS 框架 | 3.x |
| shadcn/ui | UI 组件库 | - |
| Radix UI | 无样式组件 | - |
| Lucide React | 图标库 | - |

---

## 🎨 主题定制

### 切换主题

点击右上角的太阳/月亮图标切换暗色/亮色模式。

### 自定义颜色

编辑 `src/index.css` 中的 CSS 变量：

```css
:root {
  --primary: 262.1 83.3% 57.8%;  /* 主色调 */
  --background: 0 0% 100%;         /* 背景色 */
  --foreground: 222.2 84% 4.9%;     /* 前景色 */
}

.dark {
  --primary: 262.1 83.3% 57.8%;
  --background: 222.2 84% 4.9%;
  --foreground: 210 40% 98%;
}
```

---

## 📝 添加新工具

1. 在 `src/components/tools/` 创建工具组件
2. 在 `src/config/tools.tsx` 中注册工具
3. 在 `src/components/layout/tool-content.tsx` 中添加路由

示例：

```tsx
// src/components/tools/my-tool.tsx
export function MyTool() {
  return (
    <div className="h-full flex flex-col p-6">
      <h2>我的工具</h2>
      {/* 工具内容 */}
    </div>
  )
}
```

```tsx
// src/config/tools.tsx
import { MyTool } from "@/components/tools/my-tool"

// 在对应分类中添加
{
  id: "my-tool",
  name: "我的工具",
  icon: <Star className="h-4 w-4" />,
  category: "dev",
  description: "这是一个自定义工具",
}
```

```tsx
// src/components/layout/tool-content.tsx
import { MyTool } from "@/components/tools/my-tool"

// 在 switch 中添加
case "my-tool":
  return <MyTool />
```

---

## 🌐 CI/CD

### GitHub Actions

项目已配置 GitHub Actions，构建产物会自动部署。

```yaml
# .github/workflows/deploy.yml
name: Deploy
on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
      - run: npm ci
      - run: npm run build
      # 添加你的部署步骤
```

---

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/amazing-feature`)
3. 提交更改 (`git commit -m 'Add amazing feature'`)
4. 推送分支 (`git push origin feature/amazing-feature`)
5. 创建 Pull Request

---

## 📄 许可证

本项目采用 [MIT 许可证](./LICENSE)。

---

## 🙏 致谢

- [Vite](https://vitejs.dev/) - 下一代前端构建工具
- [React](https://react.dev/) - 用于构建用户界面的 JavaScript 库
- [Tailwind CSS](https://tailwindcss.com/) - 一个实用优先的 CSS 框架
- [shadcn/ui](https://ui.shadcn.com/) - 精美的可访问组件
- [Lucide](https://lucide.dev/) - 美丽的开源图标

---

<div align="center">

如果你觉得这个项目有帮助，请给我一个 ⭐️

Made with ❤️ by [lzwanan](https://github.com/lzwanan)

</div>
