# Nested & Inner Classes

[[!Kotlin]]

```Kotlin

class OuterClass {  
    private var name: String = "Mr. X"  
  
 inner class InnerClass {  
        var description: String = "code inside nested class"  
 private var id: Int = 101  
 fun foo() {  
            println("name is $name") //доступно для Inner class  
 println("Id is $id")  
        }  
    }  
}  
  
  
fun main(args: Array<String>) {  
    //nested class must be initialized  
 println(OuterClass().InnerClass().description)  
    //accessing property  
  
 val obj = OuterClass().InnerClass()//object creation  
 obj.foo()//access member function  
  
}

```

Пример для **Inner Class.** 
**Nested Class** - примерно все то же самое, только у него нет доступа к методам и параметрам "родительского" класса