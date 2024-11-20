# Safe type casting
[[!Kotlin]]


```Kotlin

fun main(args: Array<String>) {  
  
    val location:Any = "Kotlin"  
    val safeString: String? = location as? String  
    val safeInt: Int? = location as? Int  
  
    println(safeString)  
    println(safeInt)  
  
}

```