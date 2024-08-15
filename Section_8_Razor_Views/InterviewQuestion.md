
# Section 8 Interview Questions and Answers

## What is the MVC pattern?

The **Model-View-Controller (MVC)** is an architectural pattern that separates an application into three main logical components: the model, the view, and the controller. It’s important to note that this pattern is unrelated to the layered pattern. MVC pattern operates on the software side, while the layered pattern dictates how and where we place our database and application servers.

In an application that follows the MVC pattern, each component has its role well specified. For example:
- **Model classes**: Hold the data and business logic. They do not deal with HTTP requests.
- **Views**: Only display information.
- **Controllers**: Handle and respond to user input and decide which model to pass to which view.

This is known as **separation of concerns**. It makes the application easier to develop and maintain as it grows in complexity.

Although MVC is one of the oldest and most prominent patterns, alternate patterns like **MVVM** (Model-View-ViewModel), **MVP** (Model-View-Presenter), and **MVA** (Model-View-Adapter) have also emerged.

## Explain the role of the various components of the MVC pattern

- **Model**: Represents all the data and business logic that the user interacts with in a web application. In ASP.NET Core, the model is represented by C# classes that store data and business logic. The 'Models' directory stores these classes. You can also create **POCO** (Plain Old CLR Object) classes for data storage, with business logic in separate model classes (also known as 'Services').

- **View**: Represents the UI logic of the application, which in web applications means the HTML sent to the user's browser. HTML code in the view can be dynamically generated using the model's data.

- **Controller**: Acts as an interface between the Model and the View. It processes business logic and incoming requests, manipulates data using the Model, and interacts with the Views to render the final output. In ASP.NET, these are C# classes that bind the model and view together. Controllers have action methods that respond to HTTP requests from the browser, retrieve data from the model, and pass it to the view for rendering.

## Explain the differences between ViewData and ViewBag

1. **ViewData** is a key-value paired Dictionary collection.
   **ViewBag** is an internally "object" type, dynamic property.

2. **ViewData** is a property of the `Microsoft.AspNetCore.Mvc.Controller` class.
   **ViewBag** is a dynamic property of the `Microsoft.AspNetCore.Mvc.Controller` class.

3. **ViewBag** internally uses **ViewData**. This means that data set in **ViewData** can be accessed using **ViewBag**, as **ViewBag** acts as syntactic sugar for easier access.

4. Type conversion is required when reading values from **ViewData**, whereas type conversion is not required when reading values from **ViewBag**.

5. The lifetime of both **ViewData** and **ViewBag** is per-request. They are deleted automatically at the end of the request processing. A new **ViewData** is created with each new request.

## Explain strongly-typed views

Strongly-typed views are tightly bound to a model. These views can receive a model object (of a specific model class) from the controller. The controller can supply the model object using the `return View(model)` method at the end of the action method.

Some advantages of strongly-typed views include:
- Using **@model** directive to mention the model class at the top of the view.
- Using strongly-typed tag helpers like **asp-for** in the views.
- Receiving **IntelliSense** support for accessing model properties.
- Compile-time checking to ensure that non-existent properties throw errors.
