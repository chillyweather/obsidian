# Lists

### Reverse list example
```kotlin
fun main() {  
    val testList: List<Int> = listOf(11, 12, 13, 14, 15, 16, 17, 18, 19, 20)  
    println(testList)  
    println(reverseList(testList))  
    println("Reversed version is ${testList.reversed()}")  
}  
  
fun reverseList(list: List<Int>): MutableList<Int> {  
    val result = mutableListOf<Int>()  
    for (i: Int in list.size - 1 downTo 0){  
        result.add(list.get(i))  
    }  
    return result  
}
```