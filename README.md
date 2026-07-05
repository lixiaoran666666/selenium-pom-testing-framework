# Selenium POM 自动化测试框架

这是一个基于 **Selenium WebDriver + TestNG + Maven** 的 Web UI 自动化测试框架示例，采用 Page Object Model 设计模式封装页面元素和业务操作，适合作为软件测试方向的练习项目和简历项目。

## 项目特点

- 使用 Selenium WebDriver 实现浏览器自动化操作。
- 使用 TestNG 组织测试用例和测试套件。
- 使用 Page Object Model 封装页面对象，提高代码可维护性。
- 使用 WebDriverManager 自动管理浏览器驱动。
- 支持 Excel 测试数据读取。
- 支持 Extent Reports 测试报告。
- 已优化登录页 Page Object，提高用例执行稳定性。

## 技术栈

- Java
- Selenium WebDriver
- TestNG
- Maven
- WebDriverManager
- Extent Reports
- Page Object Model

## 项目结构

```text
.
├── src/main/java/com/actoJava/qa/base/       # 测试基类和浏览器初始化
├── src/main/java/com/actoJava/qa/pages/      # Page Object 页面对象
├── src/main/java/com/actoJava/qa/util/       # 工具类和报告配置
├── src/main/resources/config/                # 配置文件
├── src/main/resources/testData/              # 测试数据
├── src/test/java/                            # 测试用例
├── src/test/resources/testSuites/            # TestNG 测试套件
└── pom.xml                                   # Maven 配置
```

## 快速启动

### 1. 准备被测网站

原项目使用一个本地示例网站作为被测系统：

```text
https://github.com/cgjangid/dummy-local-website
```

将被测网站启动后，在配置文件中修改访问地址。

### 2. 修改配置

编辑：

```text
src/main/resources/config/config.properties
```

配置浏览器类型和被测系统地址，例如：

```properties
browser=CHROME
url=http://localhost:8080
```

### 3. 编译项目

```bash
mvn -DskipTests compile
```

### 4. 执行测试

```bash
mvn test
```

也可以通过 TestNG XML 文件运行指定测试套件：

```text
src/test/resources/testSuites/
```

## 本次改造点

在 `LoginPage.java` 中增加了 `isLoginActionAvailable()` 方法，用于判断登录输入框和按钮是否可用；同时在登录前清空邮箱和密码输入框，减少连续执行用例时旧数据残留带来的影响。

## 适合简历描述

- 基于 Selenium + TestNG + Maven 搭建 Web UI 自动化测试框架，采用 Page Object Model 封装页面元素和业务操作。
- 使用 WebDriverManager 自动管理浏览器驱动，结合 TestNG 测试套件组织端到端测试流程。
- 优化登录页 Page Object，增加登录动作可用性断言和输入框清理逻辑，提高自动化用例稳定性。

## 后续可扩展方向

- 增加失败截图和日志收集。
- 增加更多登录失败、表单校验、注册流程测试用例。
- 接入 Jenkins 或 GitHub Actions，实现自动化测试流水线。
