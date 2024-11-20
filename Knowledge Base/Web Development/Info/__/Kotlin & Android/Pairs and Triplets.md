# Pairs And Triplets


### Pair
```kotlin
val equipment = "fishnet" to "catching fish"
val(tool, use) = equipment

println(equipment.first)
fishnet

println("I use $tool for $use")
I use fishnet for catching fish
```

```kotlin
val (a, b) = Pair(1, "x")
println(a) // 1
println(b) // x
```

first, second

1. toString()
2. toList()

```kotlin
//хорошо подходят для вывода нескольких результатов функций одновременно

fun giveMeATool(): Pair<String, String> {
     return ("fishnet" to "catching")
 }

val(tool, use) = giveMeATool()

println(tool)
fishnet

println(use)
catching
```

### Triple
```kotlin
val (a, b, c) = Triple(2, "x", listOf(null))
println(a) // 2
println(b) // x
println(c) // [null]
```

first, second, third

1. toString()
2. toList()

```kotlin
class Book {  
 var title: String = "Bible"  
 var author: String = "Moses"  
 var year: String = "1200BC"  
  
 fun tAndA(): Pair<String, String> {  
        return title to author  
 }  
  
 fun fullData(): Triple<String, String, String> {  
     return Triple(title, author, year)  
 }  
  
}  
  
fun main() {  
    val bible = Book()  
    val data1 = bible.tAndA()  
    println(data1)  
    val data2 = bible.fullData()  
    println("Here is your ${data2.first} written by " +  
        "${data2.second} in" +  
        " year ${data2.third}") 
}
```