# R Programming Development Specifications

---

## **1. Code Structure and Formatting**
### **1.1 Indentation**
- Use 2 spaces for indentation, avoid tabs.
- Keep the line length within **80-100 characters**.

### **1.2 Spacing**
- Add spaces around operators (e.g., `=`, `<-`, `+`), such as:
  ```r
  x <- 10
  y <- x + 5
  ```
- Do not add spaces between function names and parentheses when calling functions, such as:
  ```r
  mean(x)
  ```

### **1.3 Comments**
- Use `#` for single-line comments and add a space after the symbol, such as:
  ```r
  # This is a comment
  x <- 42  # Variable assignment
  ```
- For longer comments, separate them with `#` lines, such as:
  ```r
  # ----------------------
  # Data Cleaning Steps
  # ----------------------
  ```

---

## **2. Naming Conventions**
### **2.1 Variable and Function Naming**
- Use **lowercase letters and underscores** (snake_case), such as:
  ```r
  average_score <- 85.5
  compute_mean <- function(x) { mean(x) }
  ```

### **2.2 Constants**
- Use uppercase letters with underscores between words, such as:
  ```r
  PI <- 3.14159
  ```

### **2.3 File and Script Naming**
- Use descriptive names following snake_case, such as:
  ```
  data_cleaning.R
  model_training.R
  ```

---

## **3. Function Design**
### **3.1 Parameters**
- Function parameter names should be meaningful. Avoid using single-letter names (like `x`), unless appropriate in a mathematical or statistical context.
- Keep parameter lists clear and concise, avoiding too many parameters.

### **3.2 Return Values**
- Functions should return a single, easily understandable data structure like a vector, list, or data frame.
- Avoid side effects (e.g., directly modifying global variables within functions).

### **3.3 Documentation**
- Each function should include documentation comments, describing its functionality, parameters, return values, etc.:
  ```r
  #' Compute the mean of a vector
  #' 
  #' @param x Numeric vector
  #' @return Numeric value, the mean of the vector
  #' @examples
  #' compute_mean(c(1, 2, 3))
  compute_mean <- function(x) {
    mean(x)
  }
  ```

---

## **4. Data Processing**
- Avoid hardcoding (e.g., manually specifying column names or indices); use functions to retrieve them dynamically.
- Prefer using `tidyverse` packages (like `dplyr` and `ggplot2`) for data processing, as they result in cleaner and more readable code.

---

## **5. Error Handling**
- Handle exceptions within functions (e.g., parameter checks):
  ```r
  compute_mean <- function(x) {
    if (!is.numeric(x)) {
      stop("Parameter x must be a numeric vector")
    }
    mean(x)
  }
  ```

---

## **6. Project Management**
### **6.1 Project Structure**
- Use RStudio projects (`.Rproj`) to manage development.
- Recommended directory structure for the project:
  ```
  project_name/
  ├── data/       # Data files
  ├── R/          # R scripts
  ├── output/     # Output files
  ├── tests/      # Test scripts
  ├── README.md   # Project description
  ├── .Rproj      # RStudio project file
  ```

### **6.2 Version Control**
- Use Git for version control.
- Commit messages should be clear and concise, such as:
  ```
  Add data cleaning module
  Fix bug in model training
  ```

---

## **7. Testing**
- Use the `testthat` package to write unit tests and ensure function correctness:
  ```r
  library(testthat)

  test_that("compute_mean works correctly", {
    expect_equal(compute_mean(c(1, 2, 3)), 2)
  })
  ```

---

## **8. Code Optimization**
- Prefer vectorized operations over explicit loops:
  ```r
  # Not recommended
  result <- numeric(length(x))
  for (i in seq_along(x)) {
    result[i] <- x[i]^2
  }

  # Recommended
  result <- x^2
  ```

- When performance is a concern, consider using `data.table` or `Rcpp`.

---

## **9. Visualization**
- Use consistent styles and themes, such as setting a unified theme in `ggplot2`:
  ```r
  library(ggplot2)
  ggplot(data, aes(x, y)) +
    geom_point() +
    theme_minimal()
  ```

---

## **10. Documentation and Collaboration**
- Use `roxygen2` to generate documentation.
- Write project description files (e.g., `README.md`) to explain project goals, dependencies, usage, etc.

--- 
