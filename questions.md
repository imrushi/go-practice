Q1. What is the total memory allocated for a value of type `example` in the following code?

```go
type example struct {
  flag bool
  counter int16
  pi float32
}
```

- A. 1 byte
- B. 7 bytes
- C. 8 bytes
- D. 11 bytes

ANS: C

Q2. How can you potentially optimize the memory allocation for a value of type `example`?

```go
type example struct {
  flag bool
  counter int16
  pi float32
}
```

- A. Compiler will optimize the code.
- B. Change the order of members within the struct from highest allocation to lowest allocation.
- C. Change the order of members within the struct from lowest allocation to highest allocation.
- D. No optimization is possible; the size is fixed.

ANS: B

Q3. In Go, if you have two types `example1` and `example2` with identical structures, can you directly assign the value of `ex1` (of type example1) to `ex2` (of type example2)?

```go
type example1 struct {
  flag bool
  counter int16
  pi float32
}
type example2 struct {
  flag bool
  counter int16
  pi float32
}
var ex1 example1
var ex2 example2
```

- A. Yes, because they have the same structure.
- B. No, they are different named types.
- C. It depends on the compiler.
- D. Only if they are declared in the same package

ANS: B

Q4. What is the minimum initial size allocated for a goroutine stack in Go?

- A. 1024 bytes
- B. 2048 bytes
- C. 4096 bytes
- D. The size is dynamically determined at runtime

ANS: B

Q5. At what stage is the size of a function's stack frame typically determined?

- A. Runtime
- B. During linking
- C. Compile time
- D. When the function is called

ANS: C

Q6. If the compiler doesn’t know the size of a value at compile time, the value has to be constructed on the heap?

- A. All variables are allocated on the heap.
- B. All variables are allocated on the stack.
- C. The allocation depends on the programmer's choice through keywords like stack and heap.
- D. The compiler allocates on the stack for values with known size at compile time, and on the heap for values with unknown size.

ANS: D

Q7. what is the name of the compiler analysis technique that determines whether a variable should be allocated on the stack or the heap?

- A. Static Memory Analysis
- B. Memory Allocation Prediction
- C. Escape Analysis
- D. Reference Tracking

ANS: C

Q8. What will be the output of below program?

```go
const (
  A1 = iota
  B1
  C1
)

fmt.Println(A1, B1, C1)
```

ANS: 0 1 2

Q9. Explain the key differences between value semantics and pointer semantics iteration in the provided code examples.

ANS: **Value Semantics**: In value semantic iteration (using for i, fruit := range strings), a copy of the original array element is assigned to the fruit variable within each loop iteration. This means any modifications to fruit won't affect the original array element. This approach creates multiple copies of the underlying data (string value) in memory, potentially for efficiency reasons.
**Pointer Semantics**: In pointer semantic iteration (using for i := range strings), the loop iterates directly over the indices of the original array. Inside the loop, strings[i] retrieves the element value by reference, meaning it points to the actual string in memory. This approach avoids unnecessary data copying but requires caution as modifying strings[i] would directly change the original array element.

Q10. What will be the output of below code?

```go
var five [5]int
four := [4]int{10, 20, 30, 40}
five = four
```

- A. The code will compile and assign the values of four to five.
- B. The code will compile and assign only the first 4 elements of four to five.
- C. The code will result in a compiler error because arrays of different sizes cannot be assigned.
- D. The code will result in a runtime error when the assignment is attempted.

ANS: C

Q11. When appending a new element to a slice in Go, what happens if the current capacity of the slice is insufficient?

- A. The append operation fails, and an error is returned.
- B. The element is directly appended to the existing slice, potentially overwriting existing data.
- C. The append function resizes the existing slice in-place to accommodate the new element.
- D. The append function creates a new slice with a larger capacity, copies the existing elements, and then appends the new element.

ANS: D

Q12. What will be the output of below snippet?

```go
slice1 := []string{"A", "B", "C", "D", "E"}
slice2 := slice1[2:4]
slice2[0] = "CHANGED"
fmt.Println(slice1)
```

ANS: [A B CHANGED D E]

Q13. What will be the output of below snippet and explain the why?

```go
slice1 := []int{1, 2, 3, 4, 5}
slice2 := slice1[2:4:5]

fmt.Printf("Slice: %v, Len: %d, Cap: %d", slice2, len(slice2), cap(slice2))
```

ANS: Slice: [3 4], Len: 2, Cap: 3
The syntax for a three index slice is [a:b:c] when b and c should be the same since
[a-b] sets the length and [a-c] sets the capacity.

Q14. Fix below program so that `arr` should be copied into `tmp`.

```go
arr := []int{1, 2, 3}
tmp := []int{}
copy(tmp, arr)
fmt.Println("tmp: ", tmp)
fmt.Println("arr: ", arr)
```

ANS: Replace `tmp` declaration with this `tmp := make([]int, len(arr))`

Q15. What character encoding does the Go compiler expect source code files to be saved in?

- A. ASCII
- B. UTF-16
- C. UTF-8
- D. The encoding doesn't matter.

ANS: C

Q16. What type of value cannot be used as a key in a Go map?

- A. String
- B. Integer
- C. Boolean
- D. Pointer

ANS: A, B, C

Q17. Write Go program to define method `Speak` and call it in `main` function?

ANS:

```go
package main

import (
  fmt
)

type Dog struct {}

// define method
func (d *Dog) Speak() {
  fmt.Println("Bark")
}

func main() {
  // method call
  d := Dog{}
  d.Speak()
}
```

Q18. What is the parameter declared between the func keyword and the method name called?

- A. Argument
- B. Modifier
- C. Receiver
- D. Definition

ANS: C

Q19. Which of the following statements accurately describes a key advantage of interfaces?

- A. Interfaces directly manage memory allocation for objects.
- B. Interfaces enforce inheritance hierarchies between types.
- C. Interfaces automatically convert between different data types.
- D. Interfaces promote loose coupling and decoupling between components.

ANS: D

Q20. What is the primary focus of interfaces in Go?

- A. Grouping data by its specific type.
- B. Defining the behavior that data can exhibit.
- C. Managing memory allocation for different data structures.
- D. Enforcing inheritance hierarchies between types.

ANS: B

Q21. How do interfaces promote code maintainability?

- A. They automatically convert between different data types.
- B. They enforce strict type checking for all variables.
- C. They decouple code from specific data implementations, making it adaptable to changes.
- D. They directly manage memory allocation for objects.

ANS: C

Q22. What type of interfaces are generally considered more reusable and less prone to change?

- A. Interfaces with concise names that focus on the behavior they describe (verbs).
- B. Interfaces with descriptive names that reflect the data type they represent (nouns).
- C. Interfaces that specify the specific state or data structure of the underlying data.
- D. Interfaces with many methods representing various functionalities.

ANS: A

Q23. In which scenario is using an interface in Go most beneficial?

- A. When you want to generalize an existing algorithm for wider applicability.
- B. When you need to hide internal implementation details from API users but require them to provide specific behaviors.
- C. When a part of your code might change in the future, and you want to decouple it from the rest of the codebase.
- D. When you want to allow users to define their own interfaces for your API.

ANS: C

Q24. What is NOT a good reason to use an interface in Go?

- A. To impose a specific behavior on functions within your codebase.
- B. To simply add complexity by introducing an extra layer of abstraction.
- C. To manage multiple internal implementations of the same functionality within your API.
- D. None of the above

ANS: B, C

Q25. Before introducing an interface in your Go code, it's important to consider:

- A. It will automatically improve the performance of your code.
- B. How the interface will clearly make the code more readable and maintainable.
- C. Whether users absolutely need to define their own interfaces for interaction with your API.
- D. None of the above

ANS: B

Q26. Write a Go program which implements the interface?

```go
package main

import "fmt"

type Shape interface {
  Area() float64
}

type Square struct {
  side float64
}

func (s Square) Area() float64 {
  return s.side * s.side
}

func main() {
  s := Square{side: 5}
  fmt.Println(s.Area()) // 25
}s
```

Q27. Go doesn't have traditional class-based inheritance, but it can still achieve a degree of polymorphism. What concept allows Go to achieve this behavior?

- A. Operator overloading
- B. Multiple inheritance
- C. Interfaces
- D. Duck typing

ANS: C

Q28. Imagine you have a function `printDetails` in Go that takes an interface as a parameter. This interface has a method `getName` that returns a string. Which of the following statements is true about `printDetails`?

- A. It can only be called with a specific pre-defined type.
- B. It can be called with any type that implements the interface with the `getName` method.
- C. It needs to know the underlying type of the argument at compile time.
- D. The implementation of `printDetails` will vary depending on the type of argument passed.

ANS: B

Q29. What is a key characteristic of a polymorphic function?

- A. It always returns the same data type, regardless of the input type.
- B. It can be overloaded with different parameter lists for different functionalities.
- C. It can operate on different data types as long as they share a common behavior or interface.
- D. It performs complex mathematical calculations.

ANS: C

Q30. Write a program for File Reading with Error Handling using Interfaces.

ANS:

```go
package main

import (
	"encoding/csv"
	"errors"
	"fmt"
	"os"
)

// Define the FileReader interface
type FileReader interface {
	ReadData() (string, error)
}

// Define the TextFileReader struct
type TextFileReader struct {
	filePath string
}

// Implement ReadData() for TextFileReader
func (r TextFileReader) ReadData() (string, error) {
	data, err := os.ReadFile(r.filePath)
	if err != nil {
		return "", errors.New(fmt.Sprintf("Error reading text file: %v", err))
	}
	return string(data), nil
}

// Define the CSVFileReader struct
type CSVFileReader struct {
	filePath string
}

// Implement ReadData() for CSVFileReader
func (r CSVFileReader) ReadData() (string, error) {
	file, err := os.Open(r.filePath)
	if err != nil {
		return "", errors.New(fmt.Sprintf("Error opening CSV file: %v", err))
	}
	defer file.Close()

	reader := csv.NewReader(file)
	records, err := reader.ReadAll()
	if err != nil {
		return "", errors.New(fmt.Sprintf("Error parsing CSV file: %v", err))
	}

	// Process CSV records (example: convert to a single string)
	var content string
	for _, record := range records {
		content += fmt.Sprintf("%s\n", record)
	}
	return content, nil
}

// Generic ReadFile function
func ReadFile(reader FileReader) (string, error) {
	data, err := reader.ReadData()
	if err != nil {
		return "", err
	}
	return data, nil
}

func main() {
	// Example usage - Text file
	textReader := TextFileReader{filePath: "data.txt"}
	data, err := ReadFile(textReader)
	if err != nil {
		fmt.Println("Error reading text file:", err)
		return
	}
	fmt.Println("Text file content:", data)

	// Example usage - CSV file
	csvReader := CSVFileReader{filePath: "data.csv"}
	data, err = ReadFile(csvReader)
	if err != nil {
		fmt.Println("Error reading CSV file:", err)
		return
	}
	fmt.Println("CSV file content:", data)
}
```

Q31. Which Go package provides the most memory-efficient way to read a file, considering minimal memory allocation during the process?

- A. io/ioutil
- B. bufio
- C. encoding/csv
- D. os

ANS: B

Q32. Consider the following code:

```go
type Person struct {
  name string
  email string
}

type Employee struct {
  Person
  employeeId int
}
```

What is the difference between this approach and embedding the `Person` type in `Employee`?

- A. Field composition creates a separate instance of Person for each Employee.
- B. Embedding promotes methods of the inner type to the outer type.
- C. Embedding reduces memory usage compared to field composition.
- D. There's no functional difference between embedding and field composition in this case.

ANS: A

Q32. Imagine you have a `User` struct with a `name` field and an `Admin` struct that embeds `User`. How do you access the `name` field within an `Admin` instance?

- A. You need to explicitly cast the `Admin` instance to `User` first.
- B. You can directly access it using `admin.name`.
- C. Embedded fields are not accessible from the outer type.
- D. You need to use a special getter method defined in `Admin`.

ANS: B

Q33. In Go, when you pass a value of a type to a function, what happens?

- A. The original value is modified within the function. (Incorrect - Value Semantics)
- B. A copy of the value is passed to the function, and changes within the function don't affect the original.
- C. Go doesn't differentiate between value and pointer semantics.
- D. None of the above

ANS: B

Q34. If you want to modify the original value passed to a function in Go, which approach is most suitable?

- A. Pass the value by reference using a pointer.
- B. Return the modified value from the function and reassign it to the original variable.
- C. There's no way to modify the original value within a function in Go.
- D. Modify the value directly within the function, and changes will be reflected in the original.

ANS: A

Q35. Which scenario is most likely to benefit from using pointers in Go?

- A. When you need to pass a simple integer value to a function.
- B. When you need to check if two variables hold the same memory address.
- C. Go requires pointers for all function arguments.
- D. When you want to modify a large data structure within a function to avoid copying.

ANS: D

Q36. In Go, how can you control access to functions and variables within a package and from outside packages?

- A. By using public/private access modifiers
- B. By declaring the function or variable with a lowercase name
- C. By declaring the function or variable with an uppercase name
- D. There's no way to restrict access; all functions and variables are globally accessible.

ANS: C

Q37. What is an import cycle in Go?

- A. When two packages import each other directly.
- B. When a package imports multiple packages from the same standard library.
- C. When a package depends on a package that doesn't exist.
- D. When a package imports itself directly or indirectly.

ANS: A

Q38. What is a good practice to avoid import cycles in Go?

- A. Use wildcard imports (e.g., import "..") extensively.
- B. Refactor code to minimize dependencies between packages.
- C. Only import packages from the standard library.
- D. There's no way to completely avoid import cycles in Go.

ANS: B

Q39. What happens when you try to compile code with an import cycle?

- A. The code will compile successfully with warnings.
- B. The compiler will ignore the cycles and continue compilation.
- C. The compiler will throw an error message indicating the circular dependency.
- D. The compiled code will run with unexpected behavior due to the cycle.

ANS: C

Q40. What is the primary purpose of type assertions in Go?

- A. To enforce type safety at compile time.
- B. To convert a value from one type to another without losing information.
- C. To safely retrieve the underlying type and value from an interface.
- D. To define new custom data types.

ANS: C

Q41. What is the syntax for a type assertion in Go, and what safety considerations are involved?

- A. `value.(targetType)` - Type assertion is always guaranteed to succeed and is safe to use without checks.
- B. `value.(targetType)` - A type assertion might fail if the actual value doesn't match the target type. It's recommended to use a type switch or `ok` variable for safety checks.
- C. `value := targetType(value)` - This syntax is incorrect for type assertions.
- D. Type assertions are not necessary when working with interfaces in Go.

ANS: B

Q42. What are alternative approaches to using type assertions in Go when working with interfaces?

- A. Explicit type checks before accessing interface methods.
- B. Defining custom type aliases for interfaces.
- C. Using type switches to determine the actual type and perform actions based on it.
- D. There are no alternatives to type assertions when dealing with interfaces.

ANS: C

Q43. What is the primary function of the `go.mod` file in a Go project?

- A. To store compiled Go code.
- B. To define unit tests for the project.
- C. To configure build settings for the Go compiler.
- D. To declare the project module name and manage dependencies on other Go modules.

ANS: D

Q44. How does the `go.mod` file relate to the `go.sum` file?

- A. They are duplicates of each other.
- B. `go.mod` manages dependencies, and `go.sum` stores the actual module code.
- C. `go.sum` lists all Go modules ever downloaded on the system, regardless of the project.
- D. `go.mod` declares dependencies, and `go.sum` stores checksums (hashes) to verify the downloaded dependencies.

ANS: D

Q45. What is the purpose of the `go mod tidy` command in Go?

- A. To download all dependencies listed in the go.mod file, regardless of usage.
- B. To remove unused dependencies from the project and update the go.mod file.
- C. To compile the Go project and generate an executable file.
- D. To manually edit the go.mod file and specify dependency versions.

ANS: B

Q46. Go doesn't have built-in constructors for structs. How can you achieve controlled initialization of a struct's fields?

- A. Define a separate function named `init` that takes the struct as an argument and modifies its fields.
- B. Use a factory function that returns a new struct instance with initialized fields.
- C. Initialize fields directly within the struct definition.
- D. There's no way to control struct initialization in Go.

ANS: B

Q47. In Go, how does error handling typically work?

- A. By returning a special error code (e.g., integer) from functions.
- B. By using exceptions like in some other languages (Java, Python).
- C. There's no built-in error handling mechanism in Go.
- D. By returning an error object that implements the built-in error interface.

ANS: D

Q48. How do you typically check for errors returned from functions in Go?

- A. By using a dedicated check_error function.
- B. By using an if statement to check if the returned value is nil.
- C. By using an if statement to check if the returned error object is not nil and then calling its Error() method.
- D. Error handling is automatic in Go, and you don't need to explicitly check for errors.

ANS: C

Q49. How do you propagate errors through a chain of function calls in Go?

- A. By modifying the original error object and returning it from each function.
- B. By wrapping the returned error object with a new error context and returning it.
- C. By ignoring errors in intermediate functions and only handling them at the end.
- D. Go doesn't allow propagating errors across function calls.

ANS: B

Q50. What is the purpose of the defer statement in Go's error handling?

- A. To define a cleanup function that executes regardless of errors.
- B. To conditionally execute code based on the presence of an error.
- C. To repeat a block of code until an error occurs.
- D. Go doesn't have a defer statement.

ANS: A

Q51. What is the primary purpose of context in Go?

- A. To manage global state across functions and packages.
- B. To propagate deadlines, cancellation signals, and values across function calls.
- C. To define error handling mechanisms for functions.
- D. To improve code readability and organization.

ANS: B

Q52. What's the difference between `context.Background()` and `context.TODO()` in Go?

- A. `context.Background()` is intended for production code, while `context.TODO()` is used for testing.
- B. `context.Background()` creates a context with a deadline, while `context.TODO()` doesn't.
- C. Both are functionally identical, but `context.TODO()` is deprecated.
- D. `context.Background()` is a root context without cancellation or deadlines, while `context.TODO()` is discouraged and has no specific meaning.

Q53. How can you cancel a context and its associated goroutines?

- A. By modifying a flag variable within the context object.
- B. By using a dedicated `cancel` function associated with the context object.
- C. Cancellation is not possible for contexts in Go.
- D. Context cancellation automatically happens when the function using the context finishes.

ANS: B

Q54. How do you associate custom values with a context in Go?

- A. By using a dedicated function like `context.WithValue(ctx context.Context, key interface{}, value interface{})`.
- B. By directly modifying the context object's fields.
- C. Values cannot be associated with contexts in Go.
- D. Values are automatically inherited from parent contexts to child contexts.

ANS: A

Q55. When should you use a mutex vs. a channel for synchronization in Go?

- A. Mutexes are better for protecting shared state from concurrent access, while channels are for communication and data exchange.
- B. Channels are always preferred for synchronization, as they are lighter-weight.
- C. Mutexes offer communication capabilities, while channels are for thread safety.
- D. There's no significant difference; both achieve the same result.

ANS: A

Q56. How can you identify potential goroutine leaks in a Go program?

- A. By checking for unused variables of type func().
- B. Manually tracking goroutine creation and ensuring proper cleanup.
- C. Using profiling tools like go tool pprof to monitor goroutine creation and termination. (Correct)
- D. Go automatically manages goroutine lifecycles, so leaks are not a concern.

ANS: C

Q60. What are the common causes of deadlocks in concurrent Go programs?

- A. Using channels only for sending without receiving.
- B. Excessive use of locks without proper unlocking mechanisms.
- C. Performing long-running operations in goroutines without proper resource management.
- D. Go's garbage collector can't handle concurrent memory access.

ANS: A, B

Q61. How can you detect and prevent race conditions in Go's concurrent programs?

- A. By relying on the garbage collector to ensure memory access consistency.
- B. Using data races detection tools like `go build -race` during compilation or testing.
- C. Implementing explicit synchronization primitives (mutexes) around all critical sections.
- D. Race conditions are not a concern in Go due to its garbage collection mechanism.

ANS: B

Q62. Explain the concept of buffered channels vs. unbuffered channels in Go's concurrency, and their use cases.

- A. Buffered channels allow concurrent sending and receiving without blocking, while unbuffered channels block until both sender and receiver are ready.
- B. Unbuffered channels are faster than buffered channels due to reduced overhead.
- C. Buffered channels are primarily for unidirectional communication, while unbuffered channels are for bidirectional.
- D. Go doesn't differentiate between buffered and unbuffered channels.

ANS: A

Q63. How can context.Context be used to manage goroutine lifetimes and cancellation in Go's concurrency model?

- A. By checking a specific flag within the context object for cancellation signals.
- B. Passing the context object to goroutines and using its Done() method to check for cancellation.
- C. Context has no role in goroutine management; cancellation is handled through dedicated functions.
- D. Context is only for passing data between goroutines, not cancellation.

ANS: B

Q64. When would you use a `sync.RWMutex` instead of a regular `sync.Mutex`?

- A. Always use `RWMutex` to improve performance, as it allows multiple readers access.
- B. `RWMutex` offers communication capabilities, while `Mutex` is for thread safety.
- C. Use `sync.Mutex` for exclusive access and `sync.RWMutex` when multiple goroutines need read-only access concurrently.
- D. There's no significant difference; both achieve the same result.

ANS: C

Q65. What is the primary purpose of `sync.WaitGroup` in Go's concurrency?

- A. To synchronize access to shared data between goroutines.
- B. To manage cancellation of goroutines based on a specific condition.
- C. To efficiently schedule goroutine execution on multiple CPU cores.
- D. To signal completion of a group of goroutines before the main program exits.

ANS: D

Q66. What problem does the `sync.Once` type solve in Go's concurrency?

- A. It ensures a specific function or block of code is executed only once, even across multiple goroutines.
- B. It allows fine-grained control over goroutine execution order.
- C. It simplifies cleanup operations by automatically managing resource disposal.
- D. It reduces memory overhead by sharing a single instance of a data structure.

ANS: A

Q67. What is the syntax for sending a value (val) to a channel (ch) and receiving a value from a channel (ch) in Go?

- A. ch <- val (send), val <- ch (receive)
- B. send(ch, val) (send), recv(ch) (receive)
- C. ch.Send(val) (send), val = ch.Recv() (receive)
- D. val := <-ch (receive), ch <- val (send)

ANS: D

Q68. What is the purpose of the select statement in Go when working with channels?

- A. To define a new channel type with custom behavior.
- B. To selectively receive from multiple channels, waiting for the first available value.
- C. To send values to multiple channels based on a condition.
- D. To create a timeout mechanism for channel operations.

ANS: B

Q69. What is the primary benefit of using atomic operations in Go?

- A. To perform complex mathematical calculations efficiently.
- B. To manage memory allocation and deallocation for objects.
- C. To ensure thread-safe access and modification of shared variables in concurrent programs.
- D. To define custom synchronization primitives beyond built-in mechanisms.

ANS: C

Q70. What is the primary advantage of using table-driven unit tests in Go?

- A. To share common setup logic for multiple test cases.
- B. To improve readability and maintainability of tests with multiple scenarios.
- C. To automatically generate test cases based on a set of parameters.
- D. To reduce the overall number of test functions required.

ANS: B

Q71. What does a typical table-driven test data structure look like in Go?

- A. A slice of strings representing different test cases.
- B. A map with test names as keys and string values as inputs.
- C. A slice of structs where each struct contains input values and expected outputs for a test case.
- D. A custom data type specifically designed for table-driven tests.

ANS: C

Q72. While any approach can be used, which popular Go testing library offers built-in support for table-driven tests?

- A. testify/suite
- B. gomock
- C. go test
- D. testify/testing

ANS: D

Q73. What is the primary benefit of using web call mocking in Go unit tests?

- A. To simulate network errors and handle error scenarios in tests.
- B. To improve the performance of unit tests by avoiding actual network calls.
- C. To test the logic of your code without relying on external dependencies.
- D. To automatically generate test data for web API endpoints.

ANS: A, C

Q74. Which popular Go library provides features for mocking HTTP interactions?

- A. testify/suite
- B. gorilla/mux
- C. goquery
- D. go-mock

ANS: D

Q75. What is the primary goal of benchmarking in Go?

- A. To ensure code functionality is correct.
- B. To measure the performance of code in terms of execution time and resource usage.
- C. To identify and fix bugs in your code.
- D. To compare different algorithms for a specific task.

ANS: B

Q76. How do you define a benchmark function in Go?

- A. By using a function named benchmark followed by the function to be measured.
- B. By decorating a function with the @Benchmark annotation.
- C. By creating a separate function that calls the function to be benchmarked and measures its execution time.
- D. Go doesn't have a built-in way to benchmark functions.

ANS: A

Q77. What are some factors to consider to avoid bias in your Go benchmarks?

A. Run benchmarks only once to save time.
B. Measure execution time in milliseconds only, ignoring other factors.
C. Run benchmarks multiple times and consider variations in results.
D. Use a fixed dataset size for all benchmark runs, regardless of the function's behavior.

ANS: C

Q78. What kind of information does the Go testing framework typically provide when running benchmarks?

- A. A simple pass/fail indicator based on execution time.
- B. Detailed execution time statistics, including mean, standard deviation, and samples per second.
- C. A comparison of the benchmark's performance against a baseline or previous runs.
- D. Code coverage information for the benchmarked functions.

ANS: B

Q79. Write a Go program using goroutines and channels that simulates alternating even and odd number printing. The program should:

- Spawn 2 goroutines: one for even numbers and one for odd numbers and print till 10.
- The even goroutine should:
  - Print even number received from the odd goroutine.
  - Send odd numbers to the odd goroutine using a channel.
- The odd goroutine should:
  - Print odd numbers received from the even goroutine.
  - Send even numbers to the even goroutine using a channel.

expected output:
even 0
odd 1
even 2
odd 3
even 4
odd 5
even 6
odd 7
even 8
odd 9

ANS: With 1 Channel :- https://go.dev/play/p/5Y1cBx7QsNS
With 2 Channel :- https://go.dev/play/p/82tMWcnaIQS

Q80. Write a program to print Map in sorted order by keys:
`map[string]int{"Alice": 23, "Eve": 2, "Bob": 25, "Vim": 10, "Noob": 30, "Bot": 8}`

ANS: https://go.dev/play/p/0bYAKh1OPFI

Q81. Write a Go REST API endpoint using the POST method. This endpoint should:

- Accept JSON data as input in the request body.
- Process the received JSON data (specific processing logic).
- Respond with a JSON object containing the processed data or an error message.
- Set appropriate HTTP headers (e.g., Content-Type: application/json).
- Implement field validation on the input JSON schema.
- Handle potential errors during JSON parsing, validation, or processing with informative error messages and appropriate HTTP status codes (e.g., 400 Bad Request, 500 Internal Server Error).

JSON Schema:

```json
{
  "name": "string",
  "age": "integer"
}
```

Processing Logic:

The API endpoint can simply:

- Validate the received JSON data against the defined schema (using a library like encoding/json or a dedicated validation library).
- If valid, extract the "name" and "age" fields from the JSON object.
- Greet the user by name and indicate their age (e.g., "Hello, [name]! You are [age] years old.").
- Convert the greeting message into a JSON object.

Q82. Implement a Go program that defines a data structure called `Person` to store a person's name (string) and age (int). Additionally, create a data structure called `Stack` that utilizes a slice of `Person` structs to function as a Last-In-First-Out (LIFO) stack.

The Stack should include the following methods:

- Push(p Person): Adds a person (p) to the top of the stack.
- Pop() (Person, bool): Removes and returns the person at the top of the stack. Returns a boolean indicating success (true) or failure (false) if the stack is empty.
- IsEmpty() bool: Checks if the stack is empty.
- IsFull() bool: Checks if the stack is full (reached its predefined capacity).

ANS: https://go.dev/play/p/MP9FLoJWm61

Q83. What is the primary purpose of profiling in Go?

- A. To identify and fix bugs in your code.
- B. To measure the performance characteristics of your code, such as execution time and memory usage.
- C. To improve the readability and maintainability of your code.
- D. To automatically generate unit tests for your functions.

ANS: B

Q84. Which type of profiling is most useful for identifying CPU bottlenecks in your Go program?

- A. Memory profiling
- B. Block profiling
- C. CPU profiling
- D. Mutex profiling

ANS: C

Q85. What are two common tools available for profiling Go programs?

A. `go build`and `go test`
B. `go tool pprof`and `goveralls`
C. `go tool pprof`and `goperf`
D. All of the above

ANS: C

Q86. How can you recover from a panic in Go?

- A. By using a `try...catch` block.
- B. By wrapping the potentially panicking code within a function that returns a custom error type.
- C. By using a `defer` function with a `recover()` call to handle the panic and potentially clean up resources.
- D. Panics are always unrecoverable and require restarting the program.

ANS: C
