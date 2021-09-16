<h1 align="center">Architecture</h1></br>
<p align="center"> 
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus lobortis aliquam eros, sed placerat justo luctus tempor. Donec venenatis accumsan consequat. Nunc ac nisl finibus, finibus urna ut, vulputate dolor. Ut tellus lectus, commodo a urna non, vehicula porta mauris. Pellentesque id ornare enim. Phasellus efficitur quis metus vel dictum. Quisque sodales diam leo, sit amet tincidunt nibh gravida ac. Nunc fringilla turpis vel porta mollis. Mauris et ex quis tellus pretium mollis a id elit.
</p>

### Table of Contents
- [app](#example)
	- [bindings](#example)
		- [ImageViewBindings](#example)
		- [ToolbarBindings](#example)
		- [...]
	- [core](#example)
		- [events](#example)
			- [CommonNavigationEvent](#example)
			- [CommonViewEvent](#example)
		- [markers](#example)
			- [FetchExtras](#example)
			- [NavigationEvent](#example)
			- [...]
		- [BaseActivity](#example)
		- [BaseFragment](#example)
		- [BaseBottomSheet](#example)
		- [BaseViewModel](#example)
		- [...]
	- [di](#example)
		- [HostModule](#example)
		- [UtilsModule](#example)
	- [ext](#example)
		- [ContextExt](#example)
		- [EdittextExt](#example)
		- [FragmentExt](#example)
		- [...]
	- [ui](#example)
		- [...]
	- [utils](#example)
		- [...]
	- [views](#example)
		- [...]
	- [--](#example)
	- [--](#example)
		 - [...]
- [data](#example)
	- [di](#example)
	- [ext](#example)
	- [utils](#example)
- [domain](#example)
	- [model](#example)
	- [repository](#example)
	- [utils](#example)



<a name="example"></a>

<a name="example"></a>
## App Layer (Presentation Layer)
<details>
The presentation layer presents the data to the User.

- Interacts with the User.
- Contains UI (Activities & Fragments).
- Depends on Domain Layer.


```text
├── ExampleRoot
  ├── Child1
    ├── Child2
    ├── Child3
    ├── ...
```
</details>


<a name="example2"></a>
## Domain Layer
<details>
The domain layer is the most inner part of our Architecture.

- Contains the Repository Interfaces.
- Contains business logics.
- Has no dependencies with the other layers.
- Stores the data classes that represent backend responses.
	
```text
├── ExampleRoot
  ├── Child1
    ├── Child2
    ├── Child3
    ├── ...
```
</details>


<a name="example2"></a>
## Data Layer
<details>


- Manages & retrieves the data from the Data Sources.
- Contains business logics.
- Contains the mapped data classes to be used inside the Views. 
- Contains the Repository Implementations.
- Contains the Mappers.
```text
├── ExampleRoot
  ├── Child1
    ├── Child2
    ├── Child3
    ├── ...
```
</details>
