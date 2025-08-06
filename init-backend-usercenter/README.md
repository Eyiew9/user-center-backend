# 用户中心初始化后端

## 📖 项目简介

用户中心后端是一个基于 Spring Boot 的用户管理系统，提供用户注册、登录、注销等核心功能。项目采用现代化的技术栈，具有高性能、易扩展的特点。

## ✨ 功能特性

- 🔐 **用户认证**：支持用户注册、登录、注销功能
- 👤 **用户管理**：用户信息查询、更新、删除
- 🔍 **用户搜索**：支持按用户名模糊搜索
- 🛡️ **权限控制**：管理员权限验证
- 📊 **数据安全**：密码加密存储，逻辑删除
- 🚀 **高性能**：基于 MyBatis Plus 的数据库操作

## 🛠️ 技术栈

- **框架**：Spring Boot 2.6.4
- **数据库**：MySQL 8.0+
- **ORM**：MyBatis Plus 3.5.1
- **语言**：Java 1.8+
- **构建工具**：Maven
- **其他**：Lombok、Apache Commons Lang3

## 📋 环境要求

- JDK 1.8+
- Maven 3.5+
- MySQL 8.0+
- Docker (可选)

## 🚀 快速开始

### 1. 克隆项目

```bash
git clone https://github.com/your-username/AiQuiz-backend.git
cd AiQuiz-backend
```

### 2. 数据库配置

1. 创建数据库：
```sql
CREATE DATABASE fwy;
```

2. 执行初始化脚本：
```bash
mysql -u root -p fwy < sql/create_table.sql
```

### 3. 配置文件

修改 `src/main/resources/application.yml` 中的数据库连接信息：

```yaml
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/fwy
    username: your_username
    password: your_password
```

### 4. 启动项目

```bash
# 使用 Maven
mvn spring-boot:run

# 或者打包后运行
mvn clean package
java -jar target/user-center-backend-0.0.1-SNAPSHOT.jar
```

### 5. Docker 部署

```bash
# 构建镜像
docker build -t aiquiz-backend .

# 运行容器
docker run -p 8080:8080 aiquiz-backend
```

## 📚 API 文档

### 基础信息
- **基础URL**: `http://localhost:8080/api`
- **Content-Type**: `application/json`

### 用户接口

#### 1. 用户注册
```http
POST /api/user/register
```

**请求体**:
```json
{
  "userAccount": "testuser",
  "userPassword": "password123",
  "checkPassword": "password123",
  "planetCode": "1"
}
```

**响应**:
```json
{
  "code": 0,
  "data": 1,
  "message": "ok"
}
```

#### 2. 用户登录
```http
POST /api/user/login
```

**请求体**:
```json
{
  "userAccount": "testuser",
  "userPassword": "password123"
}
```

**响应**:
```json
{
  "code": 0,
  "data": {
    "id": 1,
    "username": "testuser",
    "userAccount": "testuser",
    "avatarUrl": null,
    "gender": null,
    "phone": null,
    "email": null,
    "userStatus": 0,
    "createTime": "2023-08-06T14:14:22",
    "updateTime": "2023-08-06T14:39:37",
    "isDelete": 0,
    "userRole": 0,
    "planetCode": "1"
  },
  "message": "ok"
}
```

#### 3. 用户注销
```http
POST /api/user/logout
```

#### 4. 获取当前用户
```http
GET /api/user/current
```

#### 5. 搜索用户 (管理员)
```http
GET /api/user/search?username=test
```

#### 6. 删除用户 (管理员)
```http
POST /api/user/delete
```

**请求体**:
```json
1
```

## 📁 项目结构

```
AiQuiz-backend/
├── src/
│   ├── main/
│   │   ├── java/com/fwy/usercenter/
│   │   │   ├── common/           # 通用响应类
│   │   │   ├── contant/          # 常量定义
│   │   │   ├── controller/       # 控制器层
│   │   │   ├── exception/        # 异常处理
│   │   │   ├── mapper/           # 数据访问层
│   │   │   ├── model/            # 数据模型
│   │   │   │   └── domain/
│   │   │   │       ├── request/  # 请求对象
│   │   │   │       └── User.java # 用户实体
│   │   │   └── service/          # 业务逻辑层
│   │   └── resources/
│   │       ├── application.yml   # 配置文件
│   │       └── mapper/           # MyBatis 映射文件
│   └── test/                     # 测试代码
├── sql/                          # 数据库脚本
├── Dockerfile                    # Docker 配置
├── pom.xml                       # Maven 配置
└── README.md                     # 项目说明
```

## 🔧 开发指南

### 添加新功能

1. 在 `model/domain` 中定义实体类
2. 在 `mapper` 中创建数据访问接口
3. 在 `service` 中实现业务逻辑
4. 在 `controller` 中暴露 API 接口

### 代码规范

- 使用 Lombok 简化代码
- 遵循 RESTful API 设计规范
- 统一异常处理和响应格式
- 添加必要的注释和文档

## 🧪 测试

```bash
# 运行所有测试
mvn test

# 运行特定测试类
mvn test -Dtest=UserServiceTest
```

## 📝 更新日志

### v0.0.1-SNAPSHOT
- ✅ 用户注册功能
- ✅ 用户登录功能
- ✅ 用户注销功能
- ✅ 用户信息查询
- ✅ 管理员权限控制
- ✅ 用户搜索功能
- ✅ 用户删除功能

## 🤝 贡献指南

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 打开 Pull Request


## 👨‍💻 作者

**房偉業** - [GitHub](https://github.com/Eyiew9)

## 🙏 致谢

- [Spring Boot](https://spring.io/projects/spring-boot) - 强大的 Java 框架
- [MyBatis Plus](https://baomidou.com/) - 优秀的 ORM 框架

---

⭐ 如果这个项目对您有帮助，请给它一个星标！

