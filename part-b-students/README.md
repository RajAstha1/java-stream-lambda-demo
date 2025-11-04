# Part B: Filtering and Sorting Students Using Streams

## Objective

Create a Java program that uses lambda expressions and stream operations to filter students scoring above 75%, sort them by marks, and display their names.

## Key Concepts

- **Stream API**: Functional-style operations on collections
- **Intermediate Operations**: filter, map, sorted
- **Terminal Operations**: forEach, collect, toList
- **Lambda Expressions**: Concise function implementations
- **Collectors**: Collecting stream results into collections

## Project Structure

```
part-b-students/
├── src/
│   ├── main/
│   │   └── java/
│   │       ├── Student.java                # Student model class
│   │       └── StudentStreamDemo.java      # Main demonstration class
│   └── test/
│       └── java/
│           └── StudentStreamTest.java      # Unit tests
├── pom.xml                   # Maven configuration
└── README.md                 # This file
```

## Features

- **Filter Students**: Using stream filter() with lambda expression for marks > 75%
- **Sort by Marks**: Using sorted() with custom comparator
- **Collect Results**: Using collect() to gather filtered students
- **Display Names**: Using forEach() to print student names
- **Stream Chaining**: Multiple operations in single stream pipeline

## Example Usage

```java
List<Student> students = Arrays.asList(
    new Student(1, "Alice", 85),
    new Student(2, "Bob", 65),
    new Student(3, "Charlie", 92),
    new Student(4, "Diana", 78)
);

// Filter and sort students using streams
students.stream()
    .filter(s -> s.getMarks() > 75)          // Filter students > 75%
    .sorted((s1, s2) -> s2.getMarks() - s1.getMarks())  // Sort by marks (descending)
    .forEach(s -> System.out.println(s.getName()));  // Display names

// Output: Charlie, Alice, Diana
```

## Stream Operations Breakdown

### filter()
```java
// Intermediate operation that returns only elements matching the predicate
.filter(s -> s.getMarks() > 75)
```

### sorted()
```java
// Intermediate operation that orders elements
.sorted((s1, s2) -> Integer.compare(s2.getMarks(), s1.getMarks()))
```

### forEach()
```java
// Terminal operation that performs an action for each element
.forEach(s -> System.out.println(s.getName()))
```

### collect()
```java
// Terminal operation that accumulates elements into a collection
.collect(Collectors.toList())
```

## Running the Code

```bash
cd part-b-students
mvn compile
mvn exec:java -Dexec.mainClass="StudentStreamDemo"
```

## Running Tests

```bash
mvn test
```

## Learning Objectives

After completing this module, you should understand:

1. How to create and chain stream operations
2. Using lambda expressions in filter conditions
3. Sorting collections with custom comparators
4. Terminal operations and stream consumption
5. Collecting stream results
6. Functional programming patterns in Java

## Common Stream Operations

| Operation | Type | Purpose |
|-----------|------|----------|
| filter() | Intermediate | Keep only matching elements |
| map() | Intermediate | Transform each element |
| sorted() | Intermediate | Sort elements |
| distinct() | Intermediate | Remove duplicates |
| limit() | Intermediate | Limit number of elements |
| forEach() | Terminal | Perform action on each element |
| collect() | Terminal | Gather elements into collection |
| findFirst() | Terminal | Get first matching element |
| count() | Terminal | Count elements |

## References

- [Java Streams API](https://docs.oracle.com/javase/8/docs/api/java/util/stream/Stream.html)
- [Lambda Expressions](https://docs.oracle.com/javase/tutorial/java/javaOO/lambdaexpressions.html)
- [Collectors Class](https://docs.oracle.com/javase/8/docs/api/java/util/stream/Collectors.html)

## Best Practices

1. Prefer streams over loops for collection processing
2. Use method references where applicable
3. Avoid side effects in lambda expressions
4. Chain operations efficiently
5. Understand intermediate vs. terminal operations

## Author Notes

This module demonstrates the power of Java's Stream API for data transformation and filtering. Streams enable functional-style programming that is both concise and efficient for collection processing tasks.
