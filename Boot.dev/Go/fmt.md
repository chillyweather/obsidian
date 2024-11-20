# Most Useful `fmt` Methods in Go

The `fmt` package in Go is incredibly versatile and provides several functions for formatted I/O. Here's a breakdown of the most useful `fmt` methods and when to use them:

## 1. **Print Functions**

These functions print to the standard output (usually the console).

- **`fmt.Print(args ...)`**  
    Prints the arguments in a default format. Arguments are concatenated without adding spaces or newlines.
    
    go
    
    Copy code
    
    `fmt.Print("Hello, ", "world!") // Output: Hello, world!`
    
- **`fmt.Println(args ...)`**  
    Similar to `Print` but adds spaces between arguments and appends a newline at the end.
    
    go
    
    Copy code
    
    `fmt.Println("Hello,", "world!") // Output: Hello, world!\n`
    
- **`fmt.Printf(format string, args ...)`**  
    Formats and prints according to a format specifier. The most flexible printing function.
    
    go
    
    Copy code
    
    `fmt.Printf("Hello, %s!\n", "world") // Output: Hello, world!`
    

## 2. **Sprintf Functions**

These are used to format strings without printing them directly (returns a string).

- **`fmt.Sprintf(format string, args ...) string`**  
    Formats a string according to the specified format and returns the result.
    
    go
    
    Copy code
    
    `s := fmt.Sprintf("Pi is approximately %.2f", 3.14159) // s = "Pi is approximately 3.14"`
    
- **`fmt.Sprintln(args ...) string`**  
    Returns the concatenation of arguments with spaces in between, ending with a newline.
    
    go
    
    Copy code
    
    `s := fmt.Sprintln("Hello,", "world!") // s = "Hello, world!\n"`
    

## 3. **Fprint Functions**

These functions print to an `io.Writer` (e.g., a file or buffer) instead of standard output.

- **`fmt.Fprint(w io.Writer, args ...)`**  
    Writes the output to the specified writer.
    
    go
    
    Copy code
    
    `var buf bytes.Buffer fmt.Fprint(&buf, "Hello, ", "world!") // buf contains: "Hello, world!"`
    
- **`fmt.Fprintf(w io.Writer, format string, args ...)`**  
    Similar to `Printf`, but writes to the provided writer instead of standard output.
    
    go
    
    Copy code
    
    `var buf bytes.Buffer fmt.Fprintf(&buf, "Pi: %.2f", 3.14159) // buf contains: "Pi: 3.14"`
    

## 4. **Errorf Function**

Useful for formatting error messages.

- **`fmt.Errorf(format string, args ...) error`**  
    Returns an `error` that formats according to the format specifier.
    
    go
    
    Copy code
    
    `err := fmt.Errorf("file not found: %s", "example.txt") fmt.Println(err) // Output: file not found: example.txt`
    

## 5. **Scanf Functions**

These functions are used for reading and parsing input.

- **`fmt.Scan(args ...)`**  
    Scans text from standard input and stores the results in the provided arguments.
    
    go
    
    Copy code
    
    `var name string fmt.Print("Enter your name: ") fmt.Scan(&name) fmt.Println("Hello,", name)`
    
- **`fmt.Scanf(format string, args ...)`**  
    Scans input according to a format string.
    
    go
    
    Copy code
    
    `var age int fmt.Print("Enter your age: ") fmt.Scanf("%d", &age) fmt.Println("You are", age, "years old.")`
    

---

## Common Format Verbs

Here are some commonly used verbs for `Printf`, `Sprintf`, and `Errorf`:

- `%v` - Default format
- `%+v` - Default format with field names for structs
- `%#v` - Go-syntax representation
- `%T` - Type of the value
- `%d` - Decimal integer
- `%f` - Floating-point number
- `%s` - String
- `%t` - Boolean

These methods give you a lot of flexibility in formatting and working with output in Go.