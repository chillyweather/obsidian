# ViewBinding

[[!Kotlin]]

связывание элементов интерфейса из activity_main.xml с логикой в MainActivity.kt

1. Добавить строку в build.gradle(:app):

```groovy

android {  
 compileSdkVersion 30  
  
 defaultConfig {  
 applicationId "com.example.ageinminutes"  
 minSdkVersion 26  
 targetSdkVersion 30  
 versionCode 1  
 versionName "1.0"  
  
 testInstrumentationRunner "androidx.test.runner.AndroidJUnitRunner"  
 }  
  
 buildTypes {  
 release {  
 minifyEnabled false  
 proguardFiles getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro'  
 }  
 } compileOptions {  
 sourceCompatibility JavaVersion.VERSION_1_8  
 targetCompatibility JavaVersion.VERSION_1_8  
 }  
 kotlinOptions {  
 jvmTarget = '1.8'  
 }  
  
  // эти три строки
 buildFeatures {  
 viewBinding true  
 }  
}

```

2. Добавить строки в MainActivity.kt

```kotlin

class MainActivity : AppCompatActivity() {  
  
 private lateinit var binding: ActivityMainBinding  // <- это
  
 override fun onCreate(savedInstanceState: Bundle?) {  
 super.onCreate(savedInstanceState)  
 binding = ActivityMainBinding.inflate(layoutInflater)  // <- это
 setContentView(binding.root)  // <- это
  
 binding.btnDatePicker.setOnClickListener {  // <- тут binding
 Toast.makeText(this, "Button works", Toast.LENGTH_LONG).show() }  
 }  
  
}

```