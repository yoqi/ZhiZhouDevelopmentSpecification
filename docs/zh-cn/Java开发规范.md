# Java 开发规范


## 变量命名

### Swagger注解


## Springboot 开发

### 项目结构

这里采用maven构建，MVC结构，项目结构如下：
```
├── src
│   ├── main
│   │   ├── java
│   │   │   └── com
│   │   │       └── example
│   │   │           └── demo
│   │   │               ├── controller
│   │   │               ├── entity
│   │   │               ├── mapper
│   │   │               ├── service
│   │   │               └── DemoApplication.java
│   │   └── resources
│   │       ├── application.properties
│   │       ├── static
│   │       └── templates
│   └── test
└── pom.xml
```

其中，`controller`用于存放控制层代码，`entity`用于存放实体类，`mapper`用于存放mapper接口，`service`用于存放业务逻辑代码，`DemoApplication.java`是项目启动类，`application.properties`是项目配置文件。

### 项目配置






