# DSA-Java

This document contains notes on Data Structures and Algorithms (DSA) with Java code. Each chapter includes notes, explanations, and references to corresponding Java implementations.

## How to Analyze Code for Complexity:

When analyzing code for complexity, consider how the number of basic operations (e.g., read, write, arithmetic operations, assignments) scales with the number of items that need to be processed. These operations directly affect performance, so it's crucial to evaluate them, especially under the worst-case scenario.

## Big O Notation

Big O notation is used to describe the complexity of an algorithm, specifically how its execution time scales with an increased number of input objects. The complexity is always based on the worst-case scenario, meaning if a method has multiple operations, the worst-case operation is considered for determining the complexity.

### Types of Big O Notation

- **O(1):** The algorithm executes in constant time, regardless of the number \( N \).
- **O(n):** The algorithm's execution time increases linearly with the number \( N \).
- **O(n^2):** The execution time increases quadratically as \( N \) increases.
- **O(n^3):** The execution time increases cubically as \( N \) increases.
- **O(n + m):** The complexity is additive, combining the complexities of two operations.

### Example: Additive Complexity

```java
void method(int n, int m) {
    for(int i = 0; i < n; i++) {
        doSomething(); // O(n)
    }
    for(int i = 0; i < m; i++) {
        doSomethingElse(); // O(m)
    }
}
```
- **O(n * m):** The complexity is multiplicative, for each iteration of loop going through to n, the second loop iterates m times.

### Example: Multiplicative Complexity

```java
void method(int n, int m) {
    for(int i = 0; i < n; i++) {
      for(int j = 0; j < m; j++) {
        doSomethingElse(); // O(m)
      }
    }
}
```
- **O(n^2+n) → O(n^2):** The complexity is multiplicative and additive, but lower order terms are ignored so it stays O(n^2).

### Example: Lower Order Terms ignored O(n^2 + n) but its read O(n^2)

```java
void method(int n) {
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            doSomethingElse(); // O(m)
        }
    }
    for(int i = 0; i < n; i++) {
        doSomething(); // O(n)
    }
}
```
### **O(log n + 1) → O(log n):** The complexity is additive, but the constant term is ignored, so it stays O(log n). Additionally, every time the number of processing elements is halved, we can represent the iterations using \( k^2 \).

### Example: Constant Terms Ignored O(log n + 1) but it’s read O(log n)

```java
void doSomething(int n) {
    for (int i = 1; i < n; ) {
        doSomething2(); // O(1) per iteration
        i = i * 2;      // i doubles each time
    }
}
```
### Explanation:

- **Loop Behavior:** The loop runs by doubling the value of `i` in each iteration (`i = i * 2`). This means that with each iteration, the number of elements to process is effectively halved.
- **Logarithmic Growth:** The number of iterations required to reach or exceed `n` is approximately `log n`.
- **Using \( k^2 \):** When analyzing such loops, each time the number of processing elements is halved, we can use the notation \( k^2 \) to represent the relationship between iterations and input size.
- **Ignoring Constants:** The constant term (`+1`), which represents the last iteration, is ignored when expressing the overall complexity.
- **Final Complexity:** Therefore, the time complexity is **O(log n)**, which indicates how the loop's runtime scales with the input size `n`.


