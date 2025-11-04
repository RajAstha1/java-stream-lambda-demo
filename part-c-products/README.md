# Part C: Stream Operations on Product Dataset

## Objective

Process a large dataset of products using Java streams for grouping, finding maximum, and calculating averages.

## Key Concepts

- **Stream API**: Functional-style processing of data
- **Collectors**: Powerful tool for collecting stream results
- **Grouping Operations**: Collecting data by categories
- **Statistical Operations**: Finding max, min, average, sum
- **Custom Collectors**: Creating collectors for specific needs
- **Parallel Streams**: Processing data in parallel for performance

## Project Structure

```
part-c-products/
├── src/
│   ├── main/
│   │   └── java/
│   │       ├── Product.java                # Product model class
│   │       ├── ProductStreamDemo.java      # Main demonstration class
│   │       ├─│ StreamOperations.java       # Custom stream operations
│   │       └── ProductAnalyzer.java        # Stream analysis utilities
│   └── test/
│       └── java/
│           └── ProductStreamTest.java      # Unit tests
├── pom.xml                   # Maven configuration
└── README.md                 # This file
```

## Features

- **Grouping by Category**: Using Collectors.groupingBy()
- **Finding Maximum Price**: Using Collectors.maxBy()
- **Calculating Average Price**: Using Collectors.averagingDouble()
- **Counting Products**: Using Collectors.counting()
- **Filtering and Mapping**: Combining filter and map operations
- **Statistical Analysis**: Getting count, sum, min, max, average
- **Partitioning Data**: Dividing data into two groups

## Example Usage

```java
List<Product> products = Arrays.asList(
    new Product(1, "Laptop", "Electronics", 1200.00),
    new Product(2, "Mouse", "Electronics", 45.00),
    new Product(3, "Desk", "Furniture", 300.00),
    new Product(4, "Chair", "Furniture", 250.00),
    new Product(5, "Monitor", "Electronics", 400.00)
);

// Group by category
Map<String, List<Product>> groupedByCategory = products.stream()
    .collect(Collectors.groupingBy(Product::getCategory));

// Get the most expensive product
Optional<Product> mostExpensive = products.stream()
    .max(Comparator.comparingDouble(Product::getPrice));

// Calculate average price
Double averagePrice = products.stream()
    .collect(Collectors.averagingDouble(Product::getPrice));

// Get statistics
DoubleSummaryStatistics stats = products.stream()
    .mapToDouble(Product::getPrice)
    .summaryStatistics();
```

## Stream Collectors Examples

### groupingBy()
```java
// Group products by category
Map<String, List<Product>> byCategory = products.stream()
    .collect(Collectors.groupingBy(Product::getCategory));

// Group by category and count
Map<String, Long> categoryCount = products.stream()
    .collect(Collectors.groupingBy(Product::getCategory, 
        Collectors.counting()));

// Group by category and get average price
Map<String, Double> categoryAvgPrice = products.stream()
    .collect(Collectors.groupingBy(Product::getCategory,
        Collectors.averagingDouble(Product::getPrice)));
```

### Statistical Operations
```java
// Get statistics in one pass
DoubleSummaryStatistics stats = products.stream()
    .mapToDouble(Product::getPrice)
    .summaryStatistics();

System.out.println("Count: " + stats.getCount());
System.out.println("Sum: " + stats.getSum());
System.out.println("Average: " + stats.getAverage());
System.out.println("Min: " + stats.getMin());
System.out.println("Max: " + stats.getMax());
```

### partitioningBy()
```java
// Partition products into expensive and non-expensive
Map<Boolean, List<Product>> expensive = products.stream()
    .collect(Collectors.partitioningBy(p -> p.getPrice() > 500));

List<Product> expensiveProducts = expensive.get(true);
List<Product> affordableProducts = expensive.get(false);
```

## Running the Code

```bash
cd part-c-products
mvn compile
mvn exec:java -Dexec.mainClass="ProductStreamDemo"
```

## Running Tests

```bash
mvn test
```

## Learning Objectives

After completing this module, you should understand:

1. Using Collectors for advanced stream operations
2. Grouping data by multiple criteria
3. Statistical analysis with streams
4. Performance considerations with large datasets
5. Custom collector implementations
6. Parallel streams for performance optimization
7. Real-world data processing patterns

## Advanced Collectors

| Collector | Purpose | Example |
|-----------|---------|----------|
| toList() | Collect to List | .collect(Collectors.toList()) |
| toSet() | Collect to Set | .collect(Collectors.toSet()) |
| toMap() | Collect to Map | .collect(Collectors.toMap(...)) |
| groupingBy() | Group by key | .collect(Collectors.groupingBy(...)) |
| partitioningBy() | Partition data | .collect(Collectors.partitioningBy(...)) |
| joining() | Join strings | .collect(Collectors.joining(",")) |
| counting() | Count elements | .collect(Collectors.counting()) |
| summingDouble() | Sum values | .collect(Collectors.summingDouble(...)) |
| averagingDouble() | Average values | .collect(Collectors.averagingDouble(...)) |
| maxBy() | Find maximum | .collect(Collectors.maxBy(...)) |
| minBy() | Find minimum | .collect(Collectors.minBy(...)) |

## Performance Tips

1. **Use Parallel Streams for Large Datasets**: For collections with millions of items
2. **Avoid Side Effects**: Keep lambda expressions pure
3. **Choose Right Collector**: Each collector has different performance characteristics
4. **Prefer Method References**: More efficient than lambda expressions
5. **Use Primitive Streams**: For numeric operations, use IntStream, DoubleStream

## Common Patterns

### Finding Top N Items
```java
products.stream()
    .sorted(Comparator.comparingDouble(Product::getPrice).reversed())
    .limit(10)
    .collect(Collectors.toList());
```

### Filtering and Collecting
```java
products.stream()
    .filter(p -> p.getPrice() > 100)
    .collect(Collectors.toList());
```

### Mapping and Collecting
```java
products.stream()
    .map(Product::getName)
    .collect(Collectors.toList());
```

## References

- [Java Collectors API](https://docs.oracle.com/javase/8/docs/api/java/util/stream/Collectors.html)
- [IntStream, LongStream, DoubleStream](https://docs.oracle.com/javase/8/docs/api/java/util/stream/package-summary.html)
- [Parallel Streams](https://docs.oracle.com/javase/tutorial/collections/streams/parallelism.html)

## Author Notes

This module demonstrates how Java Streams and Collectors provide powerful tools for complex data processing operations. The ability to group, aggregate, and analyze large datasets efficiently makes Streams essential for modern Java development. The advanced use of collectors enables declarative, functional-style data processing that is both readable and performant.
