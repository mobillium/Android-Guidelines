# UI Guideline
### Table of Contents
1. [Creating Layouts & Views using XML](#creating_layouts)
2. [Theming](#theming)

<a name="creating_layouts"></a>
## Creating Layouts & Views using XML

We are creating the layout files using XML with ConstraintLayout.
We avoid using the nested views as much as we can. Instead of that, we prefer the flat view hierarchy.


##

### We are preferring the View Binding library for binding the views.
#### What are the benefits of the View Binding?

View Binding generates binding classes for all layouts in the app,
so you don't have to use the findViewById method anymore, instead of this
you can simply call the view by typing binding.viewName.tag
View bindings are type-safe, it will always create the object according to the
view types. So if you created a Button in the layout, then the
ViewBinding creates a Button object inside the binding instance
and it will use the id of the View as the reference name
of the generated object.

#### Conclusion

**The advantages of the view binding are**

- It only references the IDs from the current layout.
- Kotlin Synthetics only supports Kotlin, while ViewBinding supports both Kotlin & Java.
- It's always null safe and it requires a lesser code than the ButterKnife.


   You can take a look for more detailed comprasion https://developer.android.com/topic/libraries/view-binding
##

We always stay away from using the hardcoded values inside the XML layouts. We prefer to get the values from the resource files like **styles.xml** , **strings.xml**.   

We are making debug the GPU Overdraw issue by enabling the **[Debug GPU Overdraw](https://developer.android.com/topic/performance/rendering/inspect-gpu-rendering)** preference on the Developer Options on our Android devices, also we are checking the UI issues by using the **[Layout Inspector](https://developer.android.com/studio/debug/layout-inspector)** 

##
MotionLayout and Animations will be added
##
- We always aiming for the reusability, we are using the include tag, or we are creating the Custom Views.
- We always staw away from use the RecyclerView inside NestedScrollView because it can disable the "recycle" function of the RecyclerView.
- We are using the Shape Drawables instead of the PNG or WEBP files. 

** Regarding the Android Documentation, we recommend to limit a vector image to a maximum **200x200** dp, otherwise it can take too long to draw, because since the vector graphics are rendered at runtime, rendering of a VectorDrawable will be slower than the PNG file.


 Our rule set when choosing SVG is
  - If it's smaller than the 200*200dp
  - If it's not contains so many detail on itself
  - If it's not contains any gradient tag.   (You can use the VectorDrawable which contains a gradient tag by creating separate VectorDrawables for the different       API levels. so that you can use the VectorDrawable which contains a gradient tag for the API >=24, and you can use the other one which doesn't contain the       gradient tag for lower API levels. )

##
<a name="theming"></a>
## Theming

### styles.xml

##
### dimens.xml

##

