# UI Guideline
## Creating Layouts & Views using XML

We are creating the layout files using XML with ConstraintLayout.
We are avoiding using the nested views as much as we can. Instead of that, we are preferring the flat view hierarchy.


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

View Binding needs lesser code than the findViewByID and ButterKnife,		


##
