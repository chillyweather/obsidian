# Classes in Kotlin

[[!Kotlin]]
#oop
Classes

### Function as a parameter
```kotlin
class Aquarium {  
    var width: Int = 20  
 var height: Int = 40  
 var length: Int = 100  
  
 // создаем параметр (переменную) с помощью геттера
 val volume: Int  
        get() = width * height * length / 1000  
  
}
```

### Secondary constructor
```kotlin
fun main() {

    val s20 = MobilePhone(
        "android",
        "samsung",
        "s20",
        8
    )

    val iphone = MobilePhone(
        "ios",
        "Apple",
        "13 pro Max",
        16
    )

    iphone.memory = 32
    iphone.stateMemorySize()
    s20.stateMemorySize()

}

class MobilePhone(osName: String, brand: String, model:String){

    var memory:Int? = null
    var brand:String? = null

    init {
        this.brand = brand
        println("Mobile phone $model made by $brand, 
			running $osName created and ready! ")
    }
	
	
	//secondary constructor 
	//с обязательным обращением к this
	//(основному конструктору)
    constructor(osName: String, 
				brand: String, 
				model:String, 
				memory: Int
				): this(osName, brand, model){
        this.memory = memory
        println("Mobile phone $model made by 
			$brand, running $osName on $memory gb of memory, 
			created and ready!")
    }

    fun stateMemorySize(){
        println("$brand's memory size is $memory"+"gb")

    }

}
```