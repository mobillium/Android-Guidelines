# Android Code Style Guideline

### Table of Contents
1. [Naming Convention](#naming)
2. [Code Formatting](#code_formatting)

<a name="naming"></a>
# 1. Naming Convention


## 1.1. File Naming
In this article we'll look into naming some project files such as classes, drawables, layouts etc.

### 1.1.1. Classes
- We are using [Upper Camel Case](https://en.wikipedia.org/wiki/Camel_case). Such as: ``ProductDetail.kt``
- Android component class names should end with component names. Such as: ``ProductDetailActivity`` or ``ChangeUserNameDialog``
- Special and numeric characters should not use in class names.

### 1.1.2. Drawables
- First of all we should decide to using in which widget the drawables. Button, BottomBar or Dialog etc.

| Asset Type   | Prefix            |		Example                  |
|--------------| ------------------|-----------------------------|
| Action bar   | `action_bar_`     | `ab_stacked.9.png`          |
| Button       | `button_`	       | `btn_send_pressed.9.png`    |
| Dialog       | `dialog_`         | `dialog_top.9.png`          |
| Divider      | `divider_`        | `divider_horizontal.9.png`  |
| Icon         | `ic_`	           | `ic_star.png`               |
| Menu         | `menu_	`          | `menu_submenu_bg.9.png`     |
| Notification | `notification_`	 | `notification_bg.9.png`     |
| Tabs         | `tab_`            | `tab_pressed.9.png`         |

- We are recommend naming icons like below;

| Asset Type                      | Prefix             | Example                      |
| --------------------------------| ----------------   | ---------------------------- |
| Icons                           | `ic_`              | `ic_star.png`                |
| Launcher icons                  | `ic_launcher`      | `ic_launcher_calendar.png`   |
| Menu icons and Action Bar icons | `ic_menu`          | `ic_menu_archive.png`        |
| Status bar icons                | `ic_stat_notify`   | `ic_stat_notify_msg.png`     |
| Tab icons                       | `ic_tab`           | `ic_tab_recent.png`          |
| Dialog icons                    | `ic_dialog`        | `ic_dialog_info.png`         |

- And in some cases, we may create drawables which using in different widgets. At this point we should name drawables with this rule;
- `[bg]_[gradient or not]_[color]_[radius amount]`
- For example; `bg_gradient_red_8dp.xml`


### 1.1.3. Layouts
Layout file names should include android component names at first of the name and there is a `_` character between the words.

| Component        | Class Name             | Layout Name                   |
| ---------------- | ---------------------- | ----------------------------- |
| Activity         | `UserProfileActivity`  | `activity_user_profile.xml`   |
| Fragment         | `SignUpFragment`       | `fragment_sign_up.xml`        |
| Dialog           | `ChangePasswordDialog` | `dialog_change_password.xml`  |
| AdapterView item | ---                    | `item_person.xml`             |
| Partial layout   | ---                    | `partial_stats_bar.xml`       |

If we creating an adapter item view, should start name of the layout with `item_`.

Sometimes we are create complex layouts. When we created complex ui pieces in another layout files, layout file name should start with `partial_`.

### 1.1.4. Variables
All of the class variable name should start with lowercase except constants and continue with camel case rule. Somthing like:
```kotlin
private val userName
private var buttonSelectItem
private var textViewUserName
```
For CONSTANT VARIABLE we should use ALL UPPER CASE SEPARATE WORD WITH UNDERSCORE.. Such as;
```kotlin
const val SELECTED_SIZE_ITEM = 1
```
When we created an android widget base variable, variable name should start with the widget name. Such as;
```kotlin
private val textViewEventTitle
private var checkBoxPcivacyPolicy
```
### 1.1.5. Functions
Functions should written in `lowerCamelCase`. Like; `setUserName`, `isEmpty`

### 1.1.6. Packages
Ther is a many of usage about package names but we recommend using all lower case in package name. Somthing like; `productdetail`, `mainoperations`

<a name="code_formatting"></a>
# 2. Code Formatting
We are look into at this article when we are coding. This section taken from official [Android Kotlin Style Guide](https://developer.android.com/kotlin/style-guide#formatting)

## 2.1. Braces
Braces are not required for `when` branches and `if` expressions which have no more than one `else` branch and which fit on a single line.

```kotlin
if (string.isEmpty()) return

val result =
    if (string.isEmpty()) DEFAULT_VALUE else string

when (value) {
    0 -> return
    // …
}
```

Braces are otherwise required for any `if`, `for`, `when` branch, `do`, and `while` statements and expressions, even when the body is empty or contains only a single statement.

```kotlin
if (string.isEmpty())
    return  // WRONG!

if (string.isEmpty()) {
    return  // Okay
}

if (string.isEmpty()) return  // WRONG
else doLotsOfProcessingOn(string, otherParametersHere)

if (string.isEmpty()) {
    return  // Okay
} else {
    doLotsOfProcessingOn(string, otherParametersHere)
}
```

### 2.1.1. When Blocks are Non-Empty
Braces follow the Kernighan and Ritchie style ("Egyptian brackets") for nonempty blocks and block-like constructs:

- No line break before the opening brace.
- Line break after the opening brace.
- Line break before the closing brace.
- Line break after the closing brace, only if that brace terminates a statement or terminates the body of a function, constructor, or named class. For example, there is no line break after the brace if it is followed by else or a comma.

### 2.1.2. When Blocks are Empty
An empty block or block-like construct must be in K&R style.

```kotlin
try {
    doSomething()
} catch (e: Exception) {} // WRONG!
```

```kotlin
try {
    doSomething()
} catch (e: Exception) {
} // Okay
```
### 2.1.3. Expression
An `if/else` conditional that is used as an expression may omit braces only if the entire expression fits on one line.

```kotlin
val value = if (string.isEmpty()) 0 else 1  // Okay
```

```kotlin
val value = if (string.isEmpty())  // WRONG!
    0
else
    1
```

```kotlin
val value = if (string.isEmpty()) { // Okay
    0
} else {
    1
}
```
## 2.2. Indentation
Each time a new block or block-like construct is opened, the indent increases by four spaces. When the block ends, the indent returns to the previous indent level. The indent level applies to both code and comments throughout the block.

Each statement is followed by a line break. Semicolons are not used.

### 2.2.1. Line Wrapping
Code has a column limit of 100 characters. Except as noted below, any line that would exceed this limit must be line-wrapped, as explained below.

Exceptions:

- Lines where obeying the column limit is not possible (for example, a long URL in KDoc)
- `package` and `import` statements
- Command lines in a comment that may be cut-and-pasted into a shell

### 2.2.2 Where to Break
The prime directive of line-wrapping is: prefer to break at a higher syntactic level. Also:

- When a line is broken at an operator or infix function name, the break comes after the operator or infix function name.
- When a line is broken at the following “operator-like” symbols, the break comes before the symbol:
  - The dot separator (`.`, `?.`).
  - The two colons of a member reference (`::`).

- A method or constructor name stays attached to the open parenthesis (`(`) that follows it.
- A comma (`,`) stays attached to the token that precedes it.
- A lambda arrow (`->`) stays attached to the argument list that precedes it.

## 2.3. Functions
When a function signature does not fit on a single line, break each parameter declaration onto its own line. Parameters defined in this format should use a single indent (+4). The closing parenthesis (`)`) and return type are placed on their own line with no additional indent.

```kotlin
fun <T> Iterable<T>.joinToString(
    separator: CharSequence = ", ",
    prefix: CharSequence = "",
    postfix: CharSequence = ""
): String {
    // …
}
```
### 2.3.1. Expression Functions
When a function contains only a single expression it can be represented as an [expression function](https://kotlinlang.org/docs/functions.html#single-expression-functions).

```kotlin
override fun toString(): String {
    return "Hey"
}
```

```kotlin
override fun toString(): String = "Hey"
```

## 2.4. Properties
When a property initializer does not fit on a single line, break after the equals sign (`=`) and use an indent.
```kotlin
private val defaultCharset: Charset? =
    EncodingRegistry.getInstance().getDefaultCharsetForPropertiesFiles(file)
```
Properties declaring a `get` and/or `set` function should place each on their own line with a normal indent (+4). Format them using the same rules as functions.
```kotlin
var directory: File? = null
    set(value) {
        // …
    }
```
Read-only properties can use a shorter syntax which fits on a single line.
```kotlin 
val defaultExtension: String get() = "kt" 
```
## 2.5. Whitespace
### 2.5.1. Vertical
A single blank line appears:
- Between consecutive members of a class: properties, constructors, functions, nested classes, etc.
  - **Exception**: A blank line between two consecutive properties (having no other code between them) is optional. Such blank lines are used as needed to create logical groupings of properties and associate properties with their backing property, if present.
  - **Exception**: Blank lines between enum constants are covered below.
- Between statements, as needed to organize the code into logical subsections.
- *Optionally* before the first statement in a function, before the first member of a class, or after the last member of a class (neither encouraged nor discouraged).
- As required by other sections of this document (such as the Structure section).

Multiple consecutive blank lines are permitted, but not encouraged or ever required.

### 2.5.2. Horizontal
Beyond where required by the language or other style rules, and apart from literals, comments, and KDoc, a single ASCII space also appears in the following places only:
- Separating any reserved word, such as `if`, `for`, or `catch` from an open parenthesis (`(`) that follows it on that line.

```kotlin
// WRONG!
for(i in 0..1) {
}
```
```kotlin
// Okay
for (i in 0..1) {
}
```
- Separating any reserved word, such as `else` or `catch`, from a closing curly brace (`}`) that precedes it on that line.

```kotlin
// WRONG!
}else {
}
```
```kotlin
// Okay
} else {
}
```
- Before any open curly brace (`{`).

```kotlin
// WRONG!
if (list.isEmpty()){
}
```
```kotlin
// Okay
if (list.isEmpty()) {
}
```
- On both sides of any binary operator.

```kotlin
// WRONG!
val two = 1+1
```
```kotlin
// Okay
val two = 1 + 1
```
  This also applies to the following “operator-like” symbols:
  - the arrow in a lambda expression (`->`).

  ```kotlin
  // WRONG!
ints.map { value->value.toString() }
  ```
  ```kotlin
  // Okay
ints.map { value -> value.toString() }
  ```
  But not:
  - the two colons (`::`) of a member reference.

  ```kotlin
  // WRONG!
val toString = Any :: toString
  ```
  ```kotlin
  // Okay
val toString = Any::toString
  ```
  - the dot separator (`.`).

  ```kotlin
  // WRONG
it . toString()
  ```
  ```kotlin
  // Okay
it.toString()
  ```
  - the range operator (`..`).

  ```kotlin
  // WRONG
 for (i in 1 .. 4) print(i)
 
  ```
  ```kotlin
   // Okay
 for (i in 1..4) print(i)
  ```
- Before a colon (`:`) only if used in a class declaration for specifying a base class or interfaces, or when used in a `where` clause for [generic constraints](https://kotlinlang.org/docs/generics.html#generic-constraints).

```kotlin
// WRONG!
class Foo: Runnable
```
```kotlin
// Okay
class Foo : Runnable
```
```kotlin
// WRONG
fun <T: Comparable> max(a: T, b: T)
```
```kotlin
// Okay
fun <T : Comparable> max(a: T, b: T)
```
```kotlin
// WRONG
fun <T> max(a: T, b: T) where T: Comparable<T>
```
```kotlin
// Okay
fun <T> max(a: T, b: T) where T : Comparable<T>
```
- After a comma (`,`) or colon (`:`).

```kotlin
// WRONG!
val oneAndTwo = listOf(1,2)
```
```kotlin
// Okay
val oneAndTwo = listOf(1, 2)
```
```kotlin
// WRONG!
class Foo :Runnable
```
```kotlin
// Okay
class Foo : Runnable
```
- On both sides of the double slash (`//`) that begins an end-of-line comment. Here, multiple spaces are allowed, but not required.

```kotlin
// WRONG!
var debugging = false//disabled by default
```
```kotlin
// Okay
var debugging = false // disabled by default
```
