# Filters

### Starts with 'p'
```kotlin
val decorations = listOf("rock", "pagoda", 
	"plastic plant", "alligator", "flowerpot")

println(decorations.filter { it[0] == 'p' })
//[pagoda, plastic plant]
```

### Filtered by content and sorted
```kotlin
val spices = listOf("curry", "pepper", "cayenne", 
	"ginger", "red curry", "green curry", "red pepper")

spices.filter { it.contains("curry") }.sortedBy { it.length }
// [curry, red curry, green curry]
```

### Filtered by first and last letter
```kotlin
val spices = listOf("curry", "pepper", "cayenne", 
	"ginger", "red curry", "green curry", "red pepper")

spices.filter { it[0]=='c' && it[it.length-1]=='e' }
//[cayenne]

spices.filter { it[0]=='c' && it[it.lastIndex]=='e' }
//[cayenne]
```

### Take first 3 elements of a list and filter
```kotlin
spices.take(3).filter { it[0]=='c' }
// [curry, cayenne]
```