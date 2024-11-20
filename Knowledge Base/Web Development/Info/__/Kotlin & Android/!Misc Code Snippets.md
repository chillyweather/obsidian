# !Misc Code Snippets

[[!Kotlin]]



## Break FOR loop
```kotlin
for (i in 0 until 10) {  
    val res = getFortuneCookie()  
    println("Your fortune is $res")  
    if (res == "Take it easy and enjoy life!") break  
}
```

##  Convert user input to Int or null
```kotlin
print("Enter your birthday:")  
val birthday = readLine()?.toIntOrNull() ?: 1
```

## Random

```kotlin

fun randomDay(): String {  
    val week = listOf<String>("Monday", "Tuesday", "Wednesday", 
		"Thursday", "Friday", "Saturday", "Sunday")  
    return week[Random.nextInt(7)]  
}
```


##  If/else

```kotlin
val temperature = 10  
val isHot = if (temperature > 50) true else false  
  
println(isHot)  
  
val message = "You are ${ if (isHot) "fried" 
	else "safe"} fish"

println(message)
```

```kotlin
fun canAddFish(	tankSize: Double, 
				currentFish: List<Int>, 
				fishSize: Int = 2, 
				hasDecorations: Boolean = true): Boolean {  
    return (tankSize * if (hasDecorations) 0.8 else 1.0) 
		>= (currentFish.sum() + fishSize)  
}
```

## Short way to write a function

```Kotlin
fun max(a: Int, b: Int) = if (a > b) a else b
```

## Создание тоста для проверки жизнеспособности кнопки

```kotlin  
fun onDigit(view: View){  
 Toast.makeText(this, "Button works", Toast.LENGTH\_SHORT).show()  
}
```

## Функция проверяющая первый символ в строке и содержание в строке определенных элементов

```kotlin
fun isOperatorAdded(value: String): Boolean {  
    return if (  ## если строка начинается с минуса - false
        value.startsWith(prefix = "-")) {  
        false  
	} else {  ## true если строка содержит один из этих символов
        value.contains("/") || value.contains("+")  
                || value.contains("-") || value.contains("\*")  
    }  
  
}
```


### [[When]]

### [[Knowledge Base/Web Development/Info/__/Kotlin & Android/Functions]]