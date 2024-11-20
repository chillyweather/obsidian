# DatePicker Project

[[!Kotlin]]

[[datePicker]]
[[date and time]]
[[simple date format]]

```kotlin

package com.example.ageinminutes  
  
import android.app.DatePickerDialog  
import android.icu.util.Calendar  
import android.os.Bundle  
import android.view.View  
import androidx.appcompat.app.AppCompatActivity  
import com.example.ageinminutes.databinding.ActivityMainBinding  
import java.text.SimpleDateFormat  
import java.util.*  
  
  
class MainActivity : AppCompatActivity() {  
  
 private lateinit var binding: ActivityMainBinding //связываем с лэйаутом  
  
 override fun onCreate(savedInstanceState: Bundle?) {  
 super.onCreate(savedInstanceState)  
 binding = ActivityMainBinding.inflate(layoutInflater)  
 setContentView(binding.root)  
  
 binding.btnDatePicker.setOnClickListener { view ->  
 clickDayPicker(view)  
  
 }  
 }  
  
 fun clickDayPicker(view: View) {  
  
 //получаем значения года, месяца и дня  
 //для передачи DatePicker val myCalendar = Calendar.getInstance()  
 val year = myCalendar.get(Calendar.YEAR)  
 val month = myCalendar.get(Calendar.MONTH)  
 val day = myCalendar.get(Calendar.DAY_OF_MONTH)  
  
  
 //открывает дейт пикер с полученными выше значениями  
 val dpd = DatePickerDialog( //загоняем все в переменную  
 this,  
 DatePickerDialog.OnDateSetListener { view, selectedYear, selectedMonth, selectedDayOfMonth ->  
//                Toast.makeText(  
//                    this,  
//                    "The chosen day is $selectedDayOfMonth, ${selectedMonth + 1},  
//                    year is $selectedYear",  
//                    Toast.LENGTH_SHORT  
//                ).show()  
  
 val selectedDate = "$selectedDayOfMonth/${selectedMonth + 1}/$selectedYear"  
  
 //pattern for simple date format  
 val sdf = SimpleDateFormat("dd/MM/yyyy", Locale.ENGLISH)  
 //convert to simple date format  
 val theDate = sdf.parse(selectedDate)  
  
 //получаем результат в миллисекундах  
 // (прошедщее время с 1 января 1970) и конвертируем в минуты val selectedDateInMinutes = theDate!!.time / 86400000  
 //получаем время прошедшее до настоящего момента  
 //с 1.1.1970 в миллисекундах val currentDate = sdf.parse(sdf.format(System.currentTimeMillis()))  
  
 val currentDateInMinutes = currentDate!!.time / 86400000  
  
 val differenceInMinutes = currentDateInMinutes - selectedDateInMinutes  
  
 binding.tvSelectedDate.text = selectedDate  
 binding.tvSelectedDateInMinutes.text = differenceInMinutes.toString()  
 }, year, month, day  
 )  
 dpd.datePicker.setMaxDate(Date().time - 86400000) //ограничиваем макс. время вчерашним днем  
 dpd.show()  
  
 }  
}

```