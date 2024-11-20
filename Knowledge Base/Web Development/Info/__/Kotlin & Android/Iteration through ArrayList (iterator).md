# Iteration through ArrayList (iterator)

[[!Kotlin]]

```Kotlin

fun main() {  
  
    val arrayList: ArrayList<String> = ArrayList<String>(5)  
    var list: MutableList<String> = mutableListOf<String>()  
  
    list.add("One")  
    list.add("Two")  
  
    arrayList.addAll(list)  
  
    println(arrayList)  
  
    val itr = arrayList.iterator()  
  
    while (itr.hasNext()) {  
        println(itr.next())  
    }  
    println("size of arrayLis = " + arrayList.size)  
  
  
}

```