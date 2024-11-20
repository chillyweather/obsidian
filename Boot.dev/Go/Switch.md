In Go, the `switch` statement provides a more concise way to write multiple `if-else` conditions. It evaluates an expression and executes the case that matches the result of the expression.

Here is the basic syntax of a `switch` statement:

```go
package main

import "fmt"

func main() {
    x := 2

    switch x {
    case 1:
        fmt.Println("x is 1")
    case 2:
        fmt.Println("x is 2")
    case 3:
        fmt.Println("x is 3")
    default:
        fmt.Println("x is something else")
    }
}
```

