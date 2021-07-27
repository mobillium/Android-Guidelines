<h1 align="center">UI Guideline</h1></br>
<p align="center"> 
You can find out the suggestions and things that we are paying attention when creating the UI elements.
</p>

### Table of Contents
1. [Creating Layouts & Views using XML](#creating_layouts)
2. [Theming](#theming)
3. [Animations](#animations)

<a name="creating_layouts"></a>
## Creating the User Interfaces

- We are creating the layout files using ConstraintLayout.
   - When using the ConstraintLayout, we take care to support layout mirroring by applying these rules.  (https://developer.android.com/training/basics/supporting-devices/languages#MirroringUpdateResources)
- We avoid from using the nested views as much as we can. Instead of that, we prefer the flat view hierarchy.
- We prefer to use the drawables(shapes, vectordrawables etc.) instead of Images.
- We always stay away from using the hardcoded values inside the XML layouts. We prefer to get the values from the resource files like **styles.xml** ,        **strings.xml**.   
- One of our most important aims when creating a layout is reusability and consistency. Therefore, we take care to use custom views and styles for using common UI elements.
- We always aim to supporting different pixel densities and providing alternative bitmaps for the different screen sizes.
- We are using the AppCompat libraries because, 
   Appcompats are (AppCompatTextView,AppCompatButton etc.) supports compatible features on older versions of the platform so they allows access to new APIs on       older API versions of the platform.
      Further Information (https://developer.android.com/jetpack/androidx/releases/appcompat) 


##

### We prefer the View Binding library for binding the views.
#### What are the benefits of the View Binding?

View Binding generates binding classes for all layouts in the app,
so you don't have to use the findViewById method anymore, instead of this
you can simply call the view by typing binding.viewName.tag
View bindings are type-safe, it will always create the object according to the
view types. So if you created a Button in the layout, then the
ViewBinding creates a Button object inside the binding instance
and it will use the id of the View as the reference name
of the generated object.


**The advantages of the view binding are**

- It only references the IDs from the current layout.
- Kotlin Synthetics only supports Kotlin, while ViewBinding supports both Kotlin & Java.
- It's always null safe and it requires a lesser code than the ButterKnife.


   You can take a look for more detailed comprasion https://developer.android.com/topic/libraries/view-binding
##

## Debugging the Views

We inspect the GPU Overdraw issue by enabling the **[Debug GPU Overdraw](https://developer.android.com/topic/performance/rendering/inspect-gpu-rendering)** preference on the Developer Options on our Android devices, also we are checking the UI issues by using the **[Layout Inspector](https://developer.android.com/studio/debug/layout-inspector)** 

##

- We always aim for the reusability, we are using the include tag, or we are creating the Custom Views or we are using the styles.
- We always stay away from use the RecyclerView inside NestedScrollView because it can disable the "recycle" function of the RecyclerView.
- We are using the Shape Drawables instead of the PNG or WEBP files. 

** Regarding the Android Documentation, we recommend to limit a vector image to a maximum **200x200** dp, otherwise it can take too long to draw, because since the vector graphics are rendered at runtime, rendering of a VectorDrawable will be slower than the PNG file.


 Our rule set when choosing SVG is
  - If it's smaller than the 200*200dp
  - If it's not contains so many detail on itself
  - If it's not contains any gradient tag.   (You can use the VectorDrawable which contains a gradient tag by creating separate VectorDrawables for the different       API levels. so that you can use the VectorDrawable which contains a gradient tag for the API >=24, and you can use the other one which doesn't contain the       gradient tag for lower API levels. )

##
<a name="theming"></a>
## Theming
- We always stay away from using the hardcoded values inside the XML layouts. We prefer to get the values from the resource files like **styles.xml** ,        **strings.xml**.   

It provides us App-level consistency and it makes it easy to create new layouts or views.





### There are some different XML files to provide a theme experience.

| Name        | Purpose |
|-------------|---------|
| styles  |    Stores the defined styles, which are attributes of the Views.     |
| colors  | Contains all the defined color codes used by the Application.       |
| themes  |    Themes are the parents of the styles. All the screens can have different themes and the themes file contains all the defined theme values.    |
| dimens  | Contains all the defined dimension values inside of it. So that we can use them for the styling.   |
| strings  | Contains all the string values used by the Application, also it can be used for Localization. |

<br>
 [Themes versus Styles](https://developer.android.com/guide/topics/ui/look-and-feel/themes#versus)


### Benefits of the theming.


-  Scenario: We want to have two TextViews with a few attributes in the same layout. 



   We were going to have this kind of code for this purpose without theming.
```gradle
<androidx.constraintlayout.widget.ConstraintLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent">
    <androidx.appcompat.widget.AppCompatTextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        android:textColor="@color/white"
        android:textSize="16sp"
        android:layout_marginStart="10dp"
        android:visibility="visible"
        android:fontFamily="@font/example_font"
        android:textAllCaps="true"
        android:gravity="start"
        android:background="@drawable/bg_purple_radius"
        android:lines="1"
        android:marqueeRepeatLimit="marquee_forever"
        />
    <androidx.appcompat.widget.AppCompatTextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintBottom_toBottomOf="parent"
        android:textColor="@color/white"
        android:textSize="16sp"
        android:layout_marginStart="10dp"
        android:visibility="visible"
        android:fontFamily="@font/example_font"
        android:textAllCaps="true"
        android:gravity="start"
        android:background="@drawable/bg_purple_radius"
        android:lines="1"
        android:marqueeRepeatLimit="marquee_forever"
        />
</androidx.constraintlayout.widget.ConstraintLayout> 
```

#### But what if we used the theming?

We will just define the attributes for single time in the styles.xml, 

```gradle
<style name="MyPerfectTextView">
        <item name="android:textColor">@color/white</item>
        <item name="android:textSize">16sp</item>
        <item name="android:layout_marginStart">10dp</item>
        <item name="android:visibility">visible</item>
        <item name="android:fontFamily">@font/example_font</item>
        <item name="android:textAllCaps">true</item>
        <item name="android:gravity">start</item>
        <item name="android:background">@drawable/bg_purple_radius</item>
        <item name="android:lines">1</item>
        <item name="android:marqueeRepeatLimit">"marquee_forever</item>
    </style>

```

It's our new Layout file! 

```gradle

<androidx.constraintlayout.widget.ConstraintLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent">
    <androidx.appcompat.widget.AppCompatTextView
        style="@style/MyPerfectTextView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        />
    <androidx.appcompat.widget.AppCompatTextView
        style="@style/MyPerfectTextView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintBottom_toBottomOf="parent"
        />
</androidx.constraintlayout.widget.ConstraintLayout>

```

So, in the end, when we think about it on the whole app level, it provides us cleaner, more readable, and reusable codes.

##

<a name="animations"></a>
## Animations
We prefer to use the MotionLayout for the Animations. MotionLayout is a layout which is a subclass of the ConstraintLayout, and has a backward compatibility to API level 14. You can create your animations by using the MotionScenes, then you can apply your MotionScenes to the MotionLayout by using the "app:layoutDescription" tag.  

For Further Information: https://developer.android.com/training/constraint-layout/motionlayout
 
 
 ##
