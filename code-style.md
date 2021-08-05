# Android Code Style Guideline

### Table of Contents
1. [Naming Convention](#naming)
2. [Ordering]
3. [Constants]
4. [Static Code Analyse Tool]
5. [Code-Formatting]

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

The prefixes determined for each widget are as follows;
- `Button` -> `btn_`
- `AactionBar` -> `ab_`
- `Dialog` -> `dialog_`
- `Divider` -> `divider_`
- `Icon` -> `ic_`
- `Menu` -> `menu_`
- `Tabs` -> `tab_`

To give an example;
 - First we add prefix and than add the purpose of this drawable. Such as; `dialog_backGround.xml` or `dialog_btn_positive` etc.
