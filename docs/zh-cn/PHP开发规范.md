# PHP开发规范



PHP开发规范通常包括代码格式、命名规范、注释规范、错误处理和安全性等方面。以下是一些常见的PHP开发规范：

### 1. **代码格式**
- **缩进**：使用 4 个空格进行缩进，不使用制表符（Tab）。
- **行宽**：每行代码不应超过 120 个字符，避免代码横向滚动。
- **空格使用**：操作符（如`=`、`+`、`-`等）两边必须有一个空格，方法参数之间用逗号隔开后要加空格。
- **大括号**：大括号（`{` 和 `}`）始终与控制结构（如 `if`, `for`）同行写在同一行，且必须使用大括号，即使只有一行代码。

  ```php
  if ($condition) {
      // do something
  }
  ```

### 2. **命名规范**
- **变量命名**：使用小写字母，单词之间使用下划线（`snake_case`）。

  ```php
  $user_name;
  $user_email;
  ```

- **类命名**：采用大驼峰命名法（`CamelCase`），首字母大写。

  ```php
  class UserProfile {}
  ```

- **方法命名**：采用小驼峰命名法（`camelCase`），首字母小写。

  ```php
  function getUserName() {}
  ```

- **常量命名**：使用全大写字母，单词之间使用下划线（`UPPER_SNAKE_CASE`）。

  ```php
  define('MAX_LIMIT', 100);
  ```

### 3. **注释规范**
- **单行注释**：使用 `//`。

  ```php
  // 这是单行注释
  ```

- **多行注释**：使用 `/* */`。

  ```php
  /*
    这是多行注释
  */
  ```

- **PHPDoc 注释**：对于类、方法和函数，推荐使用 PHPDoc 风格的注释，详细描述参数、返回值和方法作用。

  ```php
  /**
   * 获取用户信息
   * 
   * @param int $user_id 用户 ID
   * @return array 用户信息
   */
  function getUserInfo($user_id) {
      // code
  }
  ```

### 4. **错误处理**
- **错误抑制符**：尽量避免使用 `@` 错误抑制符，优先使用异常处理（try-catch）和日志记录。
- **异常处理**：通过 `try-catch` 块来捕获异常并处理。

  ```php
  try {
      // some code that may throw exception
  } catch (Exception $e) {
      echo 'Caught exception: ',  $e->getMessage(), "\n";
  }
  ```

- **日志记录**：使用适当的日志记录库（如 Monolog）来记录错误信息。

### 5. **安全性**
- **SQL 注入防范**：使用预处理语句（Prepared Statements）防止 SQL 注入。

  ```php
  $stmt = $pdo->prepare('SELECT * FROM users WHERE email = :email');
  $stmt->execute(['email' => $email]);
  ```

- **XSS 攻击防范**：对输出的数据进行适当的 HTML 转义，防止跨站脚本攻击（XSS）。

  ```php
  echo htmlspecialchars($user_input, ENT_QUOTES, 'UTF-8');
  ```

- **CSRF 防范**：使用 CSRF token 来防止跨站请求伪造攻击。

### 6. **编码风格**
- **空行使用**：代码块之间使用空行分隔，以提高可读性。
- **函数长度**：每个函数的代码行数应保持适当，避免过长的函数，推荐每个函数处理单一任务。

### 7. **版本控制与分支管理**
- **Git 使用规范**：使用清晰的 commit 信息，遵循规范化的分支管理流程（如 Git Flow）。

  ```bash
  git commit -m "修复用户登录 bug"
  ```

- **避免提交敏感信息**：确保不会在 Git 中提交密码、密钥等敏感数据，使用 `.gitignore` 忽略不必要的文件。

### 8. **自动化工具**
- **代码格式化**：使用工具如 `PHP_CodeSniffer` 来自动化检查代码风格。
- **依赖管理**：使用 Composer 管理依赖，避免手动管理第三方库。

### 9. **数据库操作规范**
- **避免直接使用 SQL 语句**：尽量避免在代码中直接写 SQL 查询，而是使用 ORM 或数据库抽象层进行封装。
- **数据校验**：在数据库操作前，进行数据有效性检查和过滤。

遵循这些开发规范有助于提高代码质量、可维护性及团队协作效率。