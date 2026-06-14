# MyWeb

基于 **Java 21 + Servlet 4.0 + MySQL** 的 Web 应用程序项目，使用 Maven 进行构建管理。

## 项目简介

MyWeb 是一个采用经典 Java Servlet 技术栈构建的 Web 应用，旨在提供一个轻量、可扩展的后端服务基础框架。项目已搭建完整的包目录结构（DAO / Entity / Service / Servlet / Utils），可直接在此架构上进行业务开发。

## 技术栈

| 类别       | 技术                         |
| ---------- | ---------------------------- |
| **语言**   | Java 21                      |
| **构建**   | Maven 3.6+                   |
| **Web**    | Servlet 4.0 (javax.servlet)  |
| **数据库** | MySQL 8.0+                   |
| **JDBC**   | MySQL Connector/J 8.3.0      |
| **部署**   | WAR -> Tomcat 9+ / Jetty 等  |
| **编码**   | UTF-8                        |
| **许可**   | Apache License 2.0           |

## 项目结构

```
myweb/
+-- src/
|   +-- main/
|       +-- java/io/github/gameLMw/myweb/
|       |   +-- dao/          # 数据访问层 (Data Access Object)
|       |   +-- entity/       # 实体类 (POJO)
|       |   +-- service/      # 业务逻辑层
|       |   +-- servlet/      # Servlet 控制器层
|       |   +-- utils/        # 工具类
|       +-- resources/
|       |   +-- db.properties # 数据库连接配置
|       +-- webapp/
|           +-- WEB-INF/
|           |   +-- web.xml   # Web 应用部署描述符 (Servlet 4.0)
|           |   +-- views/    # JSP 视图目录 (待开发)
|           +-- css/          # 样式文件目录
|           +-- images/       # 图片资源目录
|           +-- js/           # JavaScript 文件目录
|           +-- index.html    # 首页
+-- target/                   # 构建输出目录
+-- .gitignore                # Git 忽略规则
+-- LICENSE                   # Apache 2.0 许可证
+-- pom.xml                   # Maven 项目配置文件
+-- README.md                 # 项目说明文档
```

## 环境要求

- **JDK** 21 或更高版本
- **Maven** 3.6 或更高版本
- **MySQL** 8.0+（如需本地运行数据库功能）
- **Servlet 容器**：Tomcat 9+ / Jetty 9+ 等

## 快速开始

### 1. 编译项目

```bash
mvn clean compile
```

### 2. 打包项目

```bash
mvn clean package
```

打包后在 target/ 目录下生成 myweb.war 文件。

### 3. 部署运行

将 target/myweb.war 部署到 Servlet 容器（如 Apache Tomcat）的 webapps 目录下，启动容器即可访问。

### 4. 数据库配置

修改 src/main/resources/db.properties，填入实际的数据库信息：

```properties
url=jdbc:mysql://localhost:3306/myweb?useSSL=false&serverTimezone=Asia/Shanghai&characterEncoding=utf8
username=你的数据库用户名
password=你的数据库密码
```

## 开发指南

项目已预置包目录分层，开发时遵循以下约定：

- **Entity**：数据库表对应的实体类
- **DAO**：封装 JDBC 数据访问操作
- **Service**：业务逻辑处理层
- **Servlet**：处理 HTTP 请求/响应
- **Utils**：通用工具类（如数据库连接池等）

示例：创建一个处理 HTTP GET 请求的 Servlet：

```java
package io.github.gameLMw.myweb.servlet;

import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

@WebServlet("/hello")
public class HelloServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp)
            throws IOException {
        resp.setContentType("text/html;charset=UTF-8");
        resp.getWriter().println("<h1>Hello, World!</h1>");
    }
}
```

## Maven 配置

- **Group ID**: io.github.gameLMw
- **Artifact ID**: myweb
- **Version**: 1.0-SNAPSHOT
- **源码与目标版本**: Java 21

完整依赖配置参见 pom.xml。

## 许可

本项目采用 Apache License 2.0 许可协议。

## 作者

- **gameLMw** -- GitHub: @gameLMw (https://github.com/gameLMw)

## 更新日志

### v1.0-SNAPSHOT

- 初始化 Maven Web 项目骨架
- 搭建分层包目录结构 (dao/entity/service/servlet/utils)
- 配置 Servlet 4.0 与 MySQL 8.3 依赖
- 配置数据库连接属性文件
- 创建静态资源目录 (css/js/images)
