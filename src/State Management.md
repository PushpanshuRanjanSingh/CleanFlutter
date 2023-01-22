### Why flutter_bloc?
1. Separate business logic from UI
2. Testable
3. Highly Maintained 
4. **Default use when you have to use throttle, debouncing and switch map basically Advance Features**

### Why cubit?
1. Subset of bloc
2. Less boilerplate
3. Easy to understand
4. **Default use cubit when you don't have idea which one to use**

![[StateManagement_flow.png]]
This Diagram shows the communication between All Layers
1. **Presentation** layer uses **Function** to interact with **Cubit**[Cubit exits in Application Layer]
2. **Application** Layer gets the **Method** called and makes the necessary **call** to **Services** in **Domain** Layer
3. Depending on the response from Domain Layer, The state of Cubit updated and then the state changes reflect on UI.

### Why Freezed?
![[Freezed.png]]
1. We use freeze in State Classes. Why ?
	1. Immutable by default
	2. Reduce lots of boilerplate and generate code with **copywith method** to generate your copy of objects automatically to implement a value equality.
	3. It is immutable, hence less error-prone.
	4. Alternative of Enum
	5. Generate Serialisation and De-Serialisation code for your model.
		- Transfer Objects to Infrastructure Layer

### Why injectable? (Dependency Injection)
![[Dependency_Injection.png]]

### Difference between BlocBuilder, BlocConsumer and BlocListener

**BlocBuilder**: It is builder widget which listen to state and return **Widget**.

```dart
BlocBuilder<BlocName,StateName>(
builder: (context,state){
 if(state is XState){ 
    return CircularProgressIndicator()
 }
}
)
```

**BlocListener**: It listens to the state during any changes happen after the first UI build done. We use it for Navigation, to show any Toast Message or Snackbar, As it doesn't return a Widget.

```dart
BlocListener<BlocName,StateName>(){
listener: (context,state){
 if(state is XState){ HelperWidget.showToast(context,"State Changed")}
},
child: BlocBuilder<BlocName,StateName>(
builder: (context,state){
 if(state is XState){ 
    return CircularProgressIndicator()
 }
}
)
}
```

**BlocConsumer**: It is a combination of BlocBuilder and BlocListener. It has listener and builder.

```dart
BlocConsumer<BlocName,StateName>(){
listener: (context,state){
 if(state is XState){ 
	 HelperWidget.showToast(context,"State Changed")
   }
},
child: BlocBuilder<BlocName,StateName>(
builder: (context,state){
 if(state is XState){ 
    return CircularProgressIndicator()
 }
}
)
}
```
