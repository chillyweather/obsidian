We can intentionally ignore return value by using “_” symbol

```Go
func getPoint() (x int, y int) {
  return 3, 4
}

// ignore y value
x, _ := getPoint()
```

The compiler will throw an error for unused var, so we have to ignore them explicitly