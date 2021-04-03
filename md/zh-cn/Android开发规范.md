# Android 开发规范

​	Android 开发可以使用各种编码语言，比如 Java, C#, Kotlin, Flutter(Dart) ，甚至是 Vue/React/PHP 等。本文将主要介绍基于 Java 开发的 Android 开发规范。遵守这个规范的要求就是，你不要觉得自己很牛，写一些稀奇古怪的东西。



### 开发模式

​	在 java/php/C#/UWP/android/vue/Angular 等开发大型项目中，**不同开发人员负责不同任务，项目分层架构，实现逻辑解耦**。

​	在 Android 开发中，传统的开发模式是所有逻辑都写在 Activity 中，一个界面一个 Activity，这很好理解，但是大型项目就会出现很多 Activity ，而且一个错误可能在很多 Activity 中出现，这样你就可能采用批量修改的方式修改大量代码。为了解决这个问题，就需要**代码复用**，抽离出公共的类，方法。



MVC

​	显示界面的叫做 View 层，业务逻辑在 Controller 层，而操作底层数据库则在 Model 层实现。这就是最简单的MVC开发模式，数据库表结构发生变化，只需要更改 Model 层代码即可。



MVP

​	MVC的思想引入到 Android 开发中，



MVVM

​	MVVM 这种思想最早是 Microsoft 提出的，基于 C# 开发 ASP.Net 项目。之后很多其他开源框架都推出类似**“数据双向绑定”** 的功能，比如 Vue/React/AngularJS，**变量值修改后，界面自动应用上**。Google总结前人思想，在 2018 推出 jetpack Andorid 开发实用工具包。希望规范 Android 开发的方式。



### 项目结构

​	首先就要讲一下 Android 开发的项目结构，采用MVC



## 禁用 lamda 表达式

​	虽然 lamda 表达式很简洁，在很多其他语言中经常使用。Java10 也开始新增 lamda 表达式这个新特性。可以减少很多代码，但是对新手理解代码原理不太友好。







## 变量命名





###



