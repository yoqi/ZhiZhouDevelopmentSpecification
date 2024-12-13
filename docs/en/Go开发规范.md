# Go Development Specification

Go, due to its high-performance characteristics, is typically used on the server side, such as for Linux resource management and distributed computing. The development guidelines emphasize clean, readable code and consistent style.

### 1. **Code Style**
- **Indentation**: Use **tabs** (instead of spaces) for code indentation.
- **Line length**: Code lines should not exceed 80 characters.
- **Empty lines**: Use empty lines appropriately to separate different functional blocks or functions.
- **Naming conventions**:
  - Use **camelCase** for naming variables, functions, and field names.
  - Use **PascalCase** (UpperCamelCase) for naming types, structs, interfaces, etc.
  - Constants should be named in **UPPER_CASE** with underscores.
  - Avoid single-letter variable names unless they are commonly used (e.g., `i`, `j`, `k` in loops).
  - Keep names concise and clear, avoiding unnecessary abbreviations.

### 2. **File and Directory Structure**
- **Main program entry**: The `main` package should be placed in the root directory of the project and kept as simple as possible.
- **Directory structure**: Use the following structure to organize your project:
  ```
  /cmd          - Main programs
  /pkg          - Reusable libraries
  /internal     - Private libraries, not to be referenced externally
  /api          - Interface definitions
  /web          - Web pages, templates, and other resources
  /scripts      - Script files
  /docs         - Documentation
  ```
- **Single responsibility for each package**: Each package should only handle one specific task. Avoid overloading a package with too many responsibilities.

### 3. **Error Handling**
- Go does not have exception handling. Error handling relies on the `error` type.
  - When a function returns an error, it should typically be checked explicitly.
  - **Handling errors** should provide clear error messages for easier debugging.
  - The common pattern for error checking is:
    ```go
    result, err := someFunction()
    if err != nil {
        log.Fatal(err)  // Or return the error
    }
    ```

### 4. **Concurrency Programming**
- **goroutine**: The basic unit for concurrency in Go. Pay attention to avoid goroutine leaks.
- **channel**: Used to pass data between goroutines. It is recommended to use named channel types for better readability.
- **select statement**: Used to choose between multiple channel operations to avoid blocking.
- Ensure synchronization when sharing data. Avoid direct memory sharing; use channels for communication.

### 5. **Interfaces and Types**

- **Interfaces**:
  - Go interfaces are implicitly implemented, meaning you don’t need to explicitly declare that a type implements an interface.
  - Interfaces should be designed to remain simple and focused.
  - Interface methods should generally not contain implementations to avoid unnecessary coupling.
- **Structs**:
  - When using structs, fields should be exported (start with uppercase letters).
  - If a struct has multiple fields, use inline comments to describe their purpose.
  - If struct fields have default values, they can be initialized via constructor functions.

### 6. **Documentation and Comments**
- **Documentation comments**: Functions, types, methods, and packages should have clear documentation comments. Comments should be full sentences and describe the function’s purpose.
- **Function and method comments**: The comment for a function should appear directly before the function declaration.
  ```go
  // CalculateSum computes the sum of two integers.
  func CalculateSum(a, b int) int {
      return a + b
  }
  ```

### 7. **Package Management**
- Use **Go modules** to manage package dependencies. Avoid using `GOPATH` and let Go modules handle project and external package management.
  - Use `go mod init` to create a module.
  - Use `go mod tidy` to clean unused dependencies.
  - Use `go get` to install external dependencies.

### 8. **Performance and Optimization**

- **Avoid unnecessary memory allocation**: Use `sync.Pool` to reuse objects and avoid frequent memory allocations.
- **Lazy loading**: Load resources only when needed, rather than preloading them.
- **Performance testing**: Use the `testing` package for performance testing. Use `go test -bench` to test performance.

### 9. **Unit Testing**
- Go provides the `testing` package to write unit tests.
  - Test function names should start with `Test`.
  - Write clear tests that cover edge cases and normal scenarios.
  - Use `go test` to run the tests.

### 10. **Dependency Injection**
- Go does not have a built-in dependency injection framework. Typically, dependency injection is done through constructor functions:
  ```go
  type Service struct {
      repo Repository
  }
  
  func NewService(r Repository) *Service {
      return &Service{repo: r}
  }
  ```

