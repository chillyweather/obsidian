[[!Kotlin]]

[High-order functions and lambdas | Kotlin (kotlinlang.org)](https://kotlinlang.org/docs/lambdas.html)


```kotlin
{println("Hi!")}()
// пример простейшей лямбды
val swam = {println("Hello!")}
swam()
// принимает аргументы, тело функции после стрелки
val dirty = 30
val waterFilter = { dirty: Int -> dirty / 2 }

//более приличная лямбда:
val dirty = 20  
val waterFilter:(Int) -> Int = {dirty -> dirty/2}
```


С этим еще надо будет разобраться подробнее, когда я столкнусь с такой необходимостью


```Kotlin

val sum = {x:Int, y:Int -> x + y}  
println(sum(5, 7))  
  
//пример при наличии некоего класса Person  
val people = listOf(Person("Alice", 29), Person("Bob", 31))  
people.maxBy { p: Person -> p.age }  
//>>>Person(name=Bob, age=31)

```


```kotlin
var dirty = 20  
  
val waterFilter: (Int) -> Int = { dirty -> dirty / 2 }  
fun feedFish(dirty: Int) = dirty + 10  
  
fun updateDirty(dirty: Int, operation: (Int) -> Int): Int {  
    return operation(dirty)  
}  
  
fun dirtyProcessor() {  
    dirty = updateDirty(dirty, waterFilter)  
    dirty = updateDirty(dirty, ::feedFish)  
    dirty = updateDirty(dirty) { dirty ->  
 		dirty + 50  
 }  
}
```