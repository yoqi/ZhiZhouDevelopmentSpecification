# C#开发规范



## 变量命名

命名空间类,接口,属性，方法,变量等。均采用驼峰命名方式。单词首字母大写。

```
public class PersonManager {}

# 接口
public interface IConvertor {}

# 异常
public class CustomException {}


private string userName;

```


## 注释


代码需要注释，方便团队协作。
```
　　/// <summary>
　　/// Get post with id
　　/// </summary>
　　/// <param name="id">post's identity</param>
　　/// <returns>post instance</returns>
    public Post GetPostById(int id)

```



```
/*******************************************************************
* Description:This is a example class
* Version: 1.0.0
* Date: 20180218 
* Author: Hiram  
* Email: hiramtan@live.com    
* Copyright @ www.wikipedia.org
*******************************************************************/
```



## Reference

[.NET 编码约定 - C# | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/fundamentals/coding-style/coding-conventions)