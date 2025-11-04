# java-stream-lambda-demo

Java programs demonstrating Lambda Expressions and Stream Operations with three distinct modules.

## Overview

This project contains comprehensive Java examples showcasing modern functional programming concepts using Lambda Expressions and Stream APIs. It's designed for developers learning advanced Java 8+ features.

## Project Structure

The repository is organized into three main modules:

```
java-stream-lambda-demo/
├── part-a-employees/          # Sorting Employee Objects with Lambda Expressions
├── part-b-students/           # Filtering and Sorting Students Using Streams
├── part-c-products/           # Stream Operations on Product Dataset
├── pom.xml                    # Maven configuration
└── README.md                  # This file
```

## Modules

### Part A: Sorting Employees with Lambda Expressions

**Objective**: Develop a Java program that sorts a list of Employee objects based on fields like name, age, or salary using lambda expressions.

**Key Concepts**:
- Lambda expressions for custom comparators
- Functional interfaces and @FunctionalInterface
- Comparator interface and its methods
- Sorting Employee objects by multiple criteria

**Location**: `part-a-employees/`

---

### Part B: Filtering and Sorting Students Using Streams

**Objective**: Create a Java program that uses lambda expressions and stream operations to filter students scoring above 75%, sort them by marks, and display their names.

**Key Concepts**:
- Stream API basics (filter, map, sorted, collect)
- Lambda expressions in stream operations
- Filtering and transforming data
- Terminal operations (forEach, collect)

**Location**: `part-b-students/`

---

### Part C: Stream Operations on Product Dataset

**Objective**: Process a large dataset of products using Java streams for grouping, finding maximum, and calculating averages.

**Key Concepts**:
- Advanced stream operations (groupingBy, maxBy, summingDouble)
- Collectors and custom collectors
- Statistical operations on streams
- Working with large datasets

**Location**: `part-c-products/`

---

## Build Configuration

This project uses **Maven** as the build tool.

### Prerequisites
- Java 8 or higher
- Maven 3.6+

### Building the Project

```bash
mvn clean install
```

### Running Tests

```bash
mvn test
```

## How to Use

1. Navigate to the specific module directory
2. Refer to the module's README.md for detailed instructions
3. Each module contains:
   - Source code examples
   - Test cases
   - Documentation

## Getting Started

### For Part A (Employees):
```bash
cd part-a-employees
mvn test
```

### For Part B (Students):
```bash
cd part-b-students
mvn test
```

### For Part C (Products):
```bash
cd part-c-products
mvn test
```

## Learning Resources

- [Java 8 Lambda Expressions](https://docs.oracle.com/javase/tutorial/java/javaOO/lambdaexpressions.html)
- [Java Streams API](https://docs.oracle.com/javase/8/docs/api/java/util/stream/Stream.html)
- [Functional Interfaces in Java](https://docs.oracle.com/javase/8/docs/api/java/util/function/package-summary.html)

## Requirements

This project demonstrates:
- ✓ Lambda expressions for functional programming
- ✓ Stream API for data processing
- ✓ Sorting and filtering collections
- ✓ Grouping and statistical operations
- ✓ Modern Java best practices

## License

MIT License - See LICENSE file for details

## Author

Created as an educational resource for learning Lambda Expressions and Stream Operations in Java.
