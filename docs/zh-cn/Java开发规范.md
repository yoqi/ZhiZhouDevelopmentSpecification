# Java 开发规范

开发过程中需要遵守的JAVA开发规范。

## 变量命名

1、文件名，类名，使用驼峰格式（如：UserSercie，UseDAO）。  
2、变量命名，首字母小写，驼峰命名（lowerCamelCase ）。  
3、常量全部大写，（如：HIGHT=12）。

单个文件，代码行数不要超过1000行。单行不要超过120个字符。

缩进采用四个空格，不得采用Tab缩进。

编码采用utf-8。

## 注释规范

单行注释 //   
多行注释 /_\*内容_/ ,在函数,类等注释采用多行注释，参考 javadoc 规范，方便各IDE识别。需写明函数的作用，参数，返回值，异常处理等。

## 日志规范

采用SLF4J 中的 API生成日志，默认保持15天。

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

## 项目结构



