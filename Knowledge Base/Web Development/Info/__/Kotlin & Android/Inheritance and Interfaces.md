# Inheritance and Interfaces

[[!Kotlin]]
#oop

```Kotlin

interface Drivable {  
    val maxSpeed: Double  
    fun drive(): String  
    fun brake() {  
        println("This drivable is braking")  
    }  
}  
  
  
open class Car(override val maxSpeed: Double, val name: String, val brand: String) : Drivable {  
    open var range: Double = 0.0  
  
 fun extendRange(amount: Double) {  
        if (amount > 0) {  
            range += amount  
        }  
    }  
  
    override fun drive(): String = "driving the interface drive"  
  	//оверрайд функции в интерфейсе
  
 open fun drive(distance: Double) {  
        println("Drove for $distance KM")  
    }  //новая функция с тем же названием
}  
  
class ElectricCar(override val maxSpeed: Double, name: String, brand: String, batteryLife: Double) :  
    Car(maxSpeed, name, brand) {  
  
    override var range = batteryLife * 6  
  
 override fun drive(distance: Double) {  
        println("Drove for $distance KM on electricity")  
        //super.drive(distance)  
 }  
  
    override fun drive():String {  
        return "Drove for $range KM on electricity" }  
  
    override fun brake() {  
        super.brake()  
        println("brake inside of electric car")  
    }  
  
}  
  
fun main() {  
  
    var myCar = Car(10.0, "A3", "Audi")  
    var eCar = ElectricCar(15.2,"S-Model", "Tesla", 85.0)  
  
    eCar.extendRange(200.0)  
  
    myCar.drive(200.0)  
    eCar.drive(200.0)  
    eCar.brake()  
  
    eCar.drive()  
  
}

```