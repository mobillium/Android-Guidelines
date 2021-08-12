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
