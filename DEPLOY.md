# 部署到群晖 (Synology NAS)

本项目已配置好 Docker 容器化，可以轻松部署到群晖 NAS 上。

## 方式一：直接复制构建产物（推荐新手）

### 步骤 1: 本地构建

```bash
cd dev-toolbox
npm install
npm run build
```

构建完成后，`dist` 目录就是静态网站文件。

### 步骤 2: 上传到群晖

1. 使用 File Station 或 SFTP 上传 `dist` 目录到群晖，例如 `/volume1/docker/dev-toolbox/`
2. 在群晖控制面板中安装 **Web Station**
3. 在 Web Station 中创建新的虚拟主机或使用共享文件夹方式

### 步骤 3: 使用 Web Station

1. 打开群晖 **控制面板** → **Web Station**
2. 点击 **PHP 设置** → 创建 PHP 8.x 配置（可选）
3. 点击 **虚拟主机** → 创建新主机
   - 选择 HTTP 端口或 HTTPS
   - 文档根目录：选择上传的 `dist` 文件夹
   - 完成配置

## 方式二：Docker 部署（推荐）

### 步骤 1: 安装 Docker 套件

在群晖 **套件中心** 安装 **Docker**。

### 步骤 2: 上传项目文件

将整个 `dev-toolbox` 文件夹上传到群晖，例如 `/volume1/docker/dev-toolbox/`

### 步骤 3: SSH 登录群晖

```bash
ssh admin@your-nas-ip
sudo -i
```

### 步骤 4: 构建并运行容器

```bash
cd /volume1/docker/dev-toolbox

# 构建镜像
docker build -t dev-toolbox .

# 运行容器
docker run -d \
  --name dev-toolbox \
  -p 3000:80 \
  --restart unless-stopped \
  dev-toolbox
```

### 步骤 5: 验证部署

打开浏览器访问 `http://your-nas-ip:3000`

## 方式三：使用 Docker Compose（推荐）

### 步骤 1-3: 同方式二

### 步骤 4: 使用 docker-compose

```bash
cd /volume1/docker/dev-toolbox

# 启动服务
docker-compose up -d

# 查看状态
docker-compose ps

# 查看日志
docker-compose logs -f
```

## 配置反向代理（可选）

如果希望使用域名访问：

1. 打开 **控制面板** → **应用程序门户** → **反向代理服务器**
2. 创建新规则：
   - 来源：自定义域名 (如 `tools.your-domain.com`)
   - 目的地：`localhost:3000`

## 常用命令

```bash
# 进入容器
docker exec -it dev-toolbox /bin/sh

# 查看日志
docker logs -f dev-toolbox

# 重启服务
docker restart dev-toolbox

# 更新部署
git pull
docker-compose down
docker-compose up -d --build
```

## 故障排除

### 端口冲突

如果 3000 端口被占用，修改 `docker-compose.yml` 中的端口映射：

```yaml
ports:
  - "8080:80"  # 改用 8080 端口
```

### 权限问题

```bash
chmod -R 777 /volume1/docker/dev-toolbox
```

### 查看容器状态

```bash
docker ps -a | grep dev-toolbox
```

## 数据备份

项目数据存储在浏览器本地（localStorage），如需备份：

1. 使用浏览器导出功能
2. 或使用浏览器的开发者工具查看 localStorage

## 更新应用

```bash
cd /volume1/docker/dev-toolbox
git pull origin main
docker-compose up -d --build
```
