# When

```kotlin



val fishName = "Herring"  
  
when(fishName.length){  
    0 -> println("Error!")   
    in 3..12 -> println("Good fish name")  
    else ->  println("OK fish name")  
}

```

<br/>

```kotlin

return when (day) {  
    "Monday" -> "flakes"  
 	"Tuesday" -> "pellets"  
 	"Wednesday" -> "redworms"  
 	"Thursday" -> "granules"  
 	"Friday" -> "mosquitoes"  
 	"Saturday" -> "lettuce"  
 	"Sunday" -> "plankton"  
 	else -> "fasting"  
}

```