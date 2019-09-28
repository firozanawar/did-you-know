# did-you-know
Here is the collection of some important points which every android developer should be aware of. 

-  **class MainActivity : AppCompatActivity() -** MainActivity extending the AppCompatActivity. In Kotlin we need to add paranthesis ()
- The *sp* abbreviation stands for *scalable pixels*.
-  When you create an ID for a view in the XML layout file, Android Studio creates an integer constant with that ID's name in the generated R class. So if you name a view roll_button, Android Studio generates and creates an integer constant called roll_button in the R class. The "@+id" prefix for the ID name tells the compiler to add that ID constant to the R class. 
-  Because AppCompatActivity is a subclass of Context, you can just use the keyword this for the context.

**Toast.makeText(this, "button clicked", Toast.LENGTH_SHORT).show()**

- SetOnClickListner of a button in kotlin

**val rollButton: Button = findViewById(R.id.roll_button)**

**rollButton.setOnClickListener { rollDice() }**

-  The string in TextView views is an instance of class CharSequence. To test its value, you need to convert it to a string:

​	**resultText.text.toString()**

-   Vectors enable your images to be drawn at many different sizes and resolutions. Bitmap images such as PNG or GIF may need to be scaled for different devices, which can result in some loss of quality. Vector drawables can scale without losing quality.
-  Global declaration in Kotlin **var diceImage : ImageView? = null or lateinit var diceImage : ImageView** The lateinit keyword promises the Kotlin compiler that the variable will be initialized before the code calls any operations on it. Therefore we don't need to initialize the variable to null here, and we can treat it as a non-nullable variable when we use it. It is a best practice to use lateinit with fields that hold views in just this way.
-   The tools namespace is used when you want to define placeholder content that is only used in the preview or the design editor in Android Studio. Attributes using the tools namespace are removed when you compile the app.
-  Namespaces are used to help resolve ambiguity when referring to attributes that have the same name. 
-  **compileSdkVersion 28** This parameter specifies the Android API level that Gradle should use to compile your app. This is the newest version of Android your app can support. 
-  **targetSdkVersion 28** This value is the most recent API that you have tested your app against.
-   **minSdkVersion 19** it determines the oldest version of Android on which your app will run. Devices that run the Android OS older than this API level cannot run your app at all.
-  AppCompatActivity is a compatibility class that ensures your activity looks the same across different platforms OS levels.
-  An important thing to note about vector drawables is that they are supported in API 21 onwards. But your app's minimum SDK is set to API 19. If you tried your app on an API 19 device or emulator, you'd see that the app seems to build and run just fine. So how does this work?

​	When you build your app, the Gradle build process generates a PNG file from each of the vector files, and those PNG files are used on any Android device below 21. These extra PNG files increase the size of your app. Unnecessarily large apps aren't great—they make downloads slower for users and take up more of their devices' limited space. Large apps also have a higher chance of being uninstalled, and of users failing to download or canceling downloads of those apps.

The good news is that there is an Android X compatibility library for vector drawables all the way back to API level 7.

Open **build.gradle (Module: app)**. Add this line to the defaultConfig section:

**vectorDrawables.useSupportLibrary = true**

**xmlns:app="http://schemas.android.com/apk/res-auto"** 

The app namespace is for attributes that come from either your custom code or from libraries and not the core Android framework.  Use android:src attribute in the <ImageView> element to be app:srcCompat. The app:srcCompat attribute uses the Android X library to support vector drawables in older versions of Android, back to API level 7.

- If you want to return int from an function in kotlin.. example

**private fun getRandomDiceImage() : Int{ }**

- Use the tools:src attribute in the <ImageView> element in your layout to display an image in only Android Studio's preview or design editor. You can then use an empty image for android:src for the final app. \
- Use the tools namespace in the Android layout file to create placeholder content or hints for layout in Android Studio. Data declared by tools attributes is not used in the final app.
-  Classes imported from the androidx package refer to the Jetpack libraries. Dependencies to Jetpack in your build.gradle file also start with androidx.
