# Part A: Sorting Employees with Lambda Expressions

## Objective

Develop a Java program that sorts a list of Employee objects based on fields like name, age, or salary using lambda expressions.

## Key Concepts

- **Lambda Expressions**: Anonymous functions that allow you to pass functions as arguments
- **Functional Interfaces**: Interfaces with a single abstract method (@FunctionalInterface)
- **Comparator Interface**: Used for custom comparison logic
- **Multiple Sorting Criteria**: Sorting by name, age, and salary in ascending/descending order

## Project Structure

```
part-a-employees/
├── src/
│   ├── main/
│   │   └── java/
│   │       ├── Employee.java              # Employee model class
│   │       ├── EmployeeSortingDemo.java    # Main demonstration class
│   │       └── EmployeeComparators.java    # Custom comparator implementations
│   └── test/
│       └── java/
│           └── EmployeeSortingTest.java    # Unit tests
├── pom.xml                   # Maven configuration
└── README.md                 # This file
```

## Features

- **Sort by Name**: Lambda expression for alphabetical sorting
- **Sort by Age**: Lambda expression for age-based sorting
- **Sort by Salary**: Lambda expression for salary-based sorting
- **Multi-level Sorting**: Combining multiple comparators using `thenComparing()`
- **Reverse Order**: Using `reversed()` for descending sorts

## Example Usage

```java
List<Employee> employees = new ArrayList<>();
employees.add(new Employee(1, "Alice", 30, 50000));
employees.add(new Employee(2, "Bob", 25, 45000));
employees.add(new Employee(3, "Charlie", 35, 60000));

// Sort by salary using lambda
employees.sort((e1, e2) -> Double.compare(e1.getSalary(), e2.getSalary()));

// Sort by name
employees.sort((e1, e2) -> e1.getName().compareTo(e2.getName()));

// Sort by age in reverse
employees.sort((e1, e2) -> Integer.compare(e2.getAge(), e1.getAge()));
```

## Lambda Expression Syntax

```java
// Basic syntax: (parameters) -> expression
(e1, e2) -> e1.getName().compareTo(e2.getName())

// With method references
Comparator.comparing(Employee::getName)
Comparator.comparing(Employee::getAge)
Comparator.comparing(Employee::getSalary)
```

## Running the Code

```bash
cd part-a-employees
mvn compile
mvn exec:java -Dexec.mainClass="EmployeeSortingDemo"
```

## Running Tests

```bash
mvn test
```

## Learning Objectives

After completing this module, you should understand:

1. How to write lambda expressions for custom comparisons
2. Using Comparator interface with lambda expressions
3. Sorting collections using sort() method
4. Method references as alternative to lambda expressions
5. Chaining comparators for multi-level sorting

## References

- [Java 8 Lambda Expressions](https://docs.oracle.com/javase/tutorial/java/javaOO/lambdaexpressions.html)
- [Comparator Interface](https://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html)
- [Java Collections API](https://docs.oracle.com/javase/8/docs/api/java/util/Collections.html)

## Author Notes

This module demonstrates the power of lambda expressions in Java 8+ for writing concise and readable code. Lambda expressions eliminate the need for verbose anonymous inner classes when implementing functional interfaces.
