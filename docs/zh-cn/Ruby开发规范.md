# Ruby 开发规范

---

## 1. **代码风格**

### 1.1 缩进和行宽
- 使用 2 个空格作为缩进，不使用 Tab。
- 每行代码不超过 80 个字符，特殊情况下可放宽至 120 个字符。

### 1.2 空格
- 方法定义时，参数括号前不加空格：
  ```ruby
  def method_name(arg1, arg2)
  ```
- 运算符两侧应加空格：
  ```ruby
  x = y + z
  ```
- 块参数前后加空格：
  ```ruby
  items.each { |item| puts item }
  ```

### 1.3 注释
- 使用 `#` 添加单行注释，完整解释代码的目的或逻辑。
- 公共类和方法应包含文档注释，描述功能和参数。

### 1.4 字符串
- 使用双引号 `"` 包含字符串，除非字符串不包含插值或转义字符时，使用单引号 `'`。

### 1.5 方法链
- 多行方法链对齐：
  ```ruby
  some_object
    .do_something
    .do_something_else
  ```

---

## 2. **命名约定**

### 2.1 变量和方法
- 使用蛇形命名法（snake_case）：`user_name`，`calculate_total`

### 2.2 类和模块
- 使用驼峰式命名法（CamelCase）：`UserAccount`，`InvoiceManager`

### 2.3 常量
- 全部大写字母，使用下划线分隔：`MAX_COUNT`，`DEFAULT_TIMEOUT`

---

## 3. **最佳实践**

### 3.1 方法定义
- 方法不应过长，推荐 10 行以内。
- 单一职责原则：每个方法只处理一种功能。

### 3.2 避免全局变量
- 避免使用 `$` 定义全局变量，使用局部变量或实例变量代替。

### 3.3 错误处理
- 使用 `begin-rescue-end` 捕获异常，提供友好的错误信息。
  ```ruby
  begin
    file = File.open("example.txt", "r")
  rescue IOError => e
    puts "File error: #{e.message}"
  end
  ```

### 3.4 使用 Ruby 的内置方法
- 优先使用内置方法和库，如 `map`、`select`、`reduce` 等，提高代码可读性和效率。

### 3.5 不使用 monkey patch
- 避免对核心类如 `String`、`Array` 添加或重写方法。必要时使用 `refinement`。

---

## 4. **测试**

### 4.1 使用 RSpec
- 推荐使用 RSpec 进行单元测试和功能测试。
- 测试用例命名清晰，描述测试目标：
  ```ruby
  describe User do
    it "returns full name" do
      user = User.new(first_name: "John", last_name: "Doe")
      expect(user.full_name).to eq("John Doe")
    end
  end
  ```

### 4.2 覆盖率
- 测试覆盖率应不低于 80%。

---

## 5. **代码组织**

### 5.1 文件结构
- 每个类和模块独立成文件，文件名与类名对应。
  ```
  lib/
    user.rb
    invoice.rb
  ```

### 5.2 模块化
- 使用模块封装通用功能，避免代码重复。
  ```ruby
  module Formatter
    def format_date(date)
      date.strftime("%Y-%m-%d")
    end
  end
  ```

### 5.3 使用 Bundler
- 使用 `Bundler` 管理依赖：
  ```ruby
  gem install bundler
  bundle init
  bundle install
  ```

---



