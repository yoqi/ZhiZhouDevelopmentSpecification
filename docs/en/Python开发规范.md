# Python Development Guidelines

---

## **1. Follow PEP 8 Code Style**
PEP 8 is the official Python code style guide:
- **Indentation**: Use 4 spaces instead of Tab.
- **Line Length**: Try to limit lines to 79 characters; docstrings and comments should be limited to 72 characters.
- **Blank Lines**:
  - Use two blank lines to separate top-level function and class definitions.
  - Use one blank line to separate methods within a class.
- **Spaces**:
  - Add a space on both sides of binary operators (`=`, `==`, etc.), but do not add spaces around `=` in function arguments (e.g., `func(arg=10)`).
  - Do not add extra spaces inside parentheses, brackets, or braces.
- **Comments**:
  - Comments should be clear and concise, using complete sentences with the first letter capitalized.
  - Add blank lines before and after block comments.
- **Naming**:
  - Use `lower_case_with_underscores` for variables, functions, and methods (e.g., `my_variable`).
  - Use all uppercase letters with underscores for constants (e.g., `MAX_SIZE`).
  - Use CamelCase for class names (e.g., `MyClass`).

---

## **2. Coding Standards**
### **File Organization**
- **Import Order**:
  1. Standard library imports (e.g., `os`, `sys`).
  2. Third-party library imports (e.g., `numpy`, `pandas`).
  3. Local module imports.
- **Avoid Circular Imports**: Refactor modules or classes to avoid dependency loops.

### **Functions and Classes**
- Keep functions short and focused on a single task.
- Use clear parameter names and provide default values where possible.
- Use `self` or `cls` in class methods to represent instance and class objects.
- Use `__init__` to define the class initialization.

### **Exception Handling**
- Catch specific exceptions instead of using a wildcard `except Exception:`.
- Always use context managers for file or resource handling, such as:
  ```python
  with open('file.txt', 'r') as f:
      data = f.read()
  ```

### **Type Annotations**
- Use type annotations to improve code readability:
  ```python
  def add(a: int, b: int) -> int:
      return a + b
  ```

---

## **3. Tools and Frameworks**
- Use code formatting tools such as **Black** or **YAPF**.
- Static code analysis tools like **Flake8** and **Pylint**.
- Type checking tools such as **mypy**.
- Automated testing tools like **pytest** and **unittest**.

---

## **4. Documentation and Comments**
- Use **docstrings** to document modules, classes, and functions. Follow the Google or NumPy style guide:
  ```python
  def add(a: int, b: int) -> int:
      """
      Adds two numbers.

      Args:
          a (int): First number.
          b (int): Second number.

      Returns:
          int: The sum of the two numbers.
      """
      return a + b
  ```
- Add necessary comments in complex code sections to avoid relying solely on code self-explanation.

---

## **5. Testing**
- Write test cases for every module or function, covering various scenarios and edge cases.
- Use assertions to check code behavior:
  ```python
  def test_add():
      assert add(2, 3) == 5
  ```
- Follow the "Single Responsibility" principle, testing one function per test.

---

## **6. Performance Optimization**
- Prefer using generators and iterators to avoid unnecessary memory usage:
  ```python
  def squares(n):
      for i in range(n):
          yield i * i
  ```
- Use built-in functions and libraries (such as `map`, `filter`, or `itertools`) to simplify code.

---

## **7. Version Control**
- Use Git for version management to ensure traceability.
- Follow branch strategies like `main` / `develop` / `feature-*`.
- Write clear commit messages:
  ```
  Add: Added user authentication feature
  Fix: Fixed crash issue on login page
  Refactor: Refactored data processing module
  ```

---

## **8. Configuration Management**
- Store sensitive information (such as API keys) in environment variables to avoid hardcoding.
- Use `.env` files and the **python-dotenv** library to load environment variables.

---

By adhering to these guidelines, you can improve the readability, maintainability, and scalability of your code. For team development, it is recommended to write project-specific coding guidelines and conduct regular code reviews.

