# ASP NET Web Forms Entity Framework

# Web Application

Consists of a set of web pages that are generated in response to user requests.

# Components of a Web App

Client - Internet - Web Server

# Components of an HTTP URL

https;// \[protocol\]\
[www.website.com/](http://www.website.com/) \[domain name\]\
home/ \[path\]\
index.html \[filename\]

# Static Web Page

- Does not change each time it is requested.
- Directly sent from the web server to the web browser when the browser requests it.

**Static webpage process**\
Web Browser &gt; HTTP Request &gt; WebServer &gt; HTTP Response (with html, js, css)

# Dynamic Web Page

- Created by a program running on an application server.
- When the application server receives requests from the browser, it runs the appropriate program. This program often needs to access the data located on a database server.
- When the application server finished processing data it generates the HTML for a web page and returns it to the web server.
- Web server returns the HMTL to the web browser as a part of an HTTP response.
- The process that starts with the browser requesting a web page and server returning it is called a **<u>round trip.</u>**

**How a web server processes a dynamic web page**

Web Browser (Client)&gt; \
Http Request (Ajax) &gt; \
Web Server (Kestrel) &gt; \
Application Server (ASP .NET CORE) &gt;\
Database Server (SQL Server)&gt;\
Application Server (ASP .NET CORE) &gt;\
Web Server (Kestrel) &gt;\
Http Response (Ajax) &gt;\
Web Browser (Client)

# What is ASP .NET

- ASP - Active Server Pages
- .NET - Part of .NET / .NET Core
- Language to develop web applications
- Can work in conjunction with any .NET language, such as C#
- Utilizes knowledge of HTML, CSS, Javascript, and more

# ASP .NET History

- ASP .NET 1.0 and 1.1 (2002)
  - Web Forms
- ASP .NET 2.0
  - New high level features: Master Pages, Themes, Navigation, Secuirty, Membership, Datasource Controls, etc.
- ASP .NET 3.5
  - LINQ 
  - AJAX 
- ASP .NET 4 (2007)
  - ASP .NET MVC (Model View Controller)
- ASP .NET CORE (2015)
  - Various Operating System Support
  - Free & Open Sourced

# ASP .NET Web Forms

Example Components

Web Forms, MVC, ASP .NET, .NET Framework (Windows Only)

- Released in 2002.
- Provides for RAD (Rapid Application Development) by letting developers build web pages by working with a design surface in a way that's similar to Windows Forms.
- Has many problems including poor performance, inadequate separation of concerns, lack of support for automated testing, and limited control over the HTML / CSS / JS that's returned to the browser.

# ASP .NET MVC (Model View Controller)

Example Components

Razor Pages, MVC, ASP .NET Core, .NET Core/.NET (Windows, Mac, Linux)

- Released in 2007.
- Uses the MVC pattern that's used by many other web dev platforms.
- Fixes many of the perceived problems with web forms to provide better performance, separation of concerns, support for automated testing, and a high degree of control over the HTML/CSS.JS that's returned to the browser in responses.
- Uses the same proprietary Windows Only ASP .NET Framework as Web Forms.

# ASP .NET Core MVC

- Released in 2015.
- Uses a service to implement the MVC pattern.
- Provides all functionality of ASP .NET MVC but with better performance, more modularity, and cleaner code.
- Built on the Open Source ASP .NET Core platform that can run on Windows, Mac, and Linux.

# Postback

- **<u>Postback</u>** - User sends the page back to the server after entering data.
- When a page is posted back to the server, the Init and Load event handlers on the page are executed.
- If you want something done only once when the page is loaded, the first time, you need to check

```csharp
if (!IsPostBack)
{
    //...
}
```

# Properties of Server Controls

- **<u>AutoPostBack</u>** - Whether the page is posted back to the server when the value of the control changes. Available for textboxes, checkboxes, and lists. \
  Buttons do not have AutoPostBack because they always post back.\
  **Default: false**
- **<u>CausesValidation</u>** - Determines whether the validation specified by validation controls should be done when a button is clicked.\
  **Default: true**
- **<u>EnableViewState</u>** - Determines whether the controls maintain its view state between the HTTP requests.\
  **Default: true**
- **<u>Runat</u>** - Indicates that the control will be processed by the ASP .NET on the server

# Validation Controls

- Validation controls are used to validate input data and display error messages to the client
- Each validation control is associated with a specific server control that is being validated, like a text box.
- There can be two or more validation controls associated with one server control, for example required field validator, and range validator.
- Validation is typically done when the focus leaves the control that is being validated, or when a user clicks on a button that has a property of CausesValidation set to true
- Drag-and-Drop from the Validation group in the toolbox

# Properties of Validation Controls

- **<u>ControlToValidate</u>** - which control is validated
- **<u>Display</u>** - 
  - **Static** - Allocates space for display on the layout. 
  - **Dynamic** - have space allocated when the error occurs.
  - **None** - Uses a validation summary control to display error messages
- **<u>ErrorMessage</u>** - Text of the error message.

# Range Validator Properties

- Type - The data type used for range checking (string, int, double, float, currency, date)
- MaximumValue
- MinimumValue
- If the user does not enter text into the control, the range validation passes. You havae to include RequiredFieldValidator as well.

# Turn Off Unobtrusive Validation

Include the following line in the Page_Load event handler

```csharp
UnobtrusiveValidationMode = 
    System.Web.UI.UnobtrusiveValidationMode.None;
```

# JQuery

Validation requires you to get Jquery, get the CDN or install it via Nuget package manager as package name 

**<span style="font-size: 15px"><u>aspnet.scriptmanager.jquery</u></span>**

# State

- State refers to the current status of the properties, variables, and overall current 'state' of the web page.
- HTTP is a stateless protocol. That means it doesnt keep state between roundtrips. Once a browser makes a request and receives a response, the app terminates and restarts. Clearing state, such as variables stored in Javascript on the client side.

# Maintaining State

Client Side

- Hidden fields on the page
- Cookies
- Query string in URL

Server Side

- Session State
- Application State
- Cache
- Database

# Session ID

- Server assigns different ID to each session.
- Stord in the session state object.
- SessionID is passed to the browser and back to the server with the next request (server can associate each request with the session it belongs to)
- Two ways of passing SessionID
  - Cookie Based
    - Default
    - Browser needs to support cookies (not really a problem)
  - Cookieless
    - SessionID is added to the URL of the requested page'

#  Entity Framework

- An Object Relational Mapping (ORM) framework
  - Abstracts the data source
  - Works with any DBMS
  - Allows developers to work with application objects (logical models) rather than database structures (physical models)
- Allows querying with LINQ
- First released in 2008
- Moved to open source in 2016 as Entity Framework Core

# Entity Frameworks Methods

- **<u>Database First Approach</u>**
  - Uses ADO .NET Entity Data Model setup wizard
  - Generates Entity Data Model as an XML file
  - Creates DbContext and Entity Classes
- **<u>Code First Approach</u>**
  - Starts with domain model: DbContext and entity classes
  - Uses Migrations to create the database

# Master Pages

A master page provides common elements for multiple pages

- File Site.Master
- More master pages can be added, right click project Add &gt; New Item &gt; Web Forms Master Page
- Master pages contains the HTML document structure
- Include content placeholder where content pages supply individual content

# Content Pages

- When you use a master page, the individual pages become content pages
- Content pages contain content elements to fill placeholder in the masterpage (ie. div is replaced in master with the contact content page div)

# Bootstrap

Common Components

- Grid System
- Navbar
- Images
- Dropdowns
- Buttons
- Modals
- Jumbotron

# Grid System

Convenient way to layout a page in logical sections

- Grid system allows up to 12 columns, but can be grouped fewer if needed (if &gt;12 will stack)
- columns contain the content
- div elements can be used as basic container

```
<div class="container">
    <div class="row">
        <div class="col-md-6">Hello World</div>
        <div class="col-md-6">Hello World</div>
    </div>
</div>
```

**Sizes:**

- xs - smartphone
- sm - tablet
- md - desktop
- lg - wide monitor

# Basic Table

```
<table class = “table”>
  <caption>Students</caption>
  <thead>
    <tr><th>First Name</th><th>Last Name</th></tr>
  </thead>
  <tbody>
    <tr><td>Jim</td><td>Munro</td></tr>
    <tr><td>Ken</td><td>Hunter</td></tr>
    <tr><td>Karen</td><td>Riley</td></tr>
  </tbody>
</table>
```

# Application Security

- Security is about encryption, authentication, and authorization.
- Encryption - data sent in encrypted form
- Authentication - validating if the users are whom they claim to be
- Authorization - are the users allowed to do what they are trying to do (ie. allow/restrict access to certain routes)

# Encryption

- Transport Layer Security TLS - Internet Protocol that uses encryption
- Replaced older Secure Socket Layer SSL - SSL is still commonly coined, when it is actually now TLS.
- TLS can determine if data has been tampered with
- Also can verify if a server or a client is who it claims to be (using certs)
- uses HTTPS

# Authentication

- Confirms users identity (ie. username, password)
- types of authentication
  - None - default
  - Windows - good for IPv4 Intranet
  - Individual User Accounts
  - Forms
  - Third Party

# Authorization

- Allowing / Denying access to pages / routes
- For example, non logged in users may not view certain pages, like My Profile.

# ASP .NET Core

- .NET Core 1 - released June 2016
  - A complete rewrite of ASP .NET turned Open Source
- Cross platform Windows Mac Linux
- ASP .NET MVC and MVC Web API were united
- No web forms (oh well lol)
- Can be used to build web apps, and services, IoT apps, mobile backends and more

# Benefits of .NET Core

- Cross platform
- open source
- high perfomance
- built in dependency injection
- hosted on a variety of webservers such as IIS, Kestrel, Docker, Apache, etc.
- No seperation of MVC and Web API Development
- Razor Page Application development
- Blazor Allows c# programming on client side
- integration with client side framwworks and libraries: Bootstrap, Angular, React, Redux, Etc.

# Types of Applications

- Razor Pages - Simple page-based programming model
- MVC - implementation of mvc pattern for ui apps
- Web API - implementation of mvc pattern for REST services
- Blazor - c# programming on client side
- SignalR - real-time client to server communcation
- gRPC - remote procedure calls that replace wcf

# Components of the MVC pattern

- Model - Consists of the code that provides the data access and business logic
- View - Consists of code that generates the user interface and presents it to the user
- Controller - consists of code that receives requests from users, gets appropriate data from the model and passes that data to the corresponding view

**Benefits of MVC**

- Easier to have a large team on same project
- Can automate testing of individual components
- makes it easier to swap out components 
- makes app easier to maintain

**Drawbacks**

- More work ( boo hoo )

# Dependency Injection (DI)

- Software pattern based on the inversion of control (IoC)
- in a sitatuion when one class objects needs another class object, there are two possible approaches
  - The dependent class's creates the needed object
  - the needed object is sent to the dependent class constructor as a parameter
- The second approach provides a more flexible solution , we can send in various types of the needed object without having to recompile the dependent class

To use DI, you code the class constructor so that it accepts a parameter of interface type

Then you create an object of that class by passing to the constructor any object that implements the interface

We can also used Dependency Injection at a method level

DI makes it easier to changes and implement unit testing

# Convention over Configuration

- Goal: Reduce the size of config files
- Programmers need to follow conventions
- conventions affect placing and naming of files

# Common naming conventions

- Controllers - All controllers should be stored in the Controllers folder/subfolder
- Controllers - All controllers should end with Controller suffix (ie. HomeController)
- Models - Stored in the Models folder of a subfolder
- Views - Should be stored in the Views folder/subfolders
- Static files - Stored in the wwwroot folder/subfolders.

Structure of the Application

- Each controller is responsible for one entity
- Model defines the entity that the controller is working with
- The controller passes the model to the view
- there can be multiple views for one controller
- a view works with one type of model: it can be a single object of the model type or a collection of objects of the model type, but not different model types
- Additional data items can be passed from the controller to a view using other tools than a model
- This leads to a well designed and efficient application

Routing and Middleware

- ASP .NET Core allows you to configure the middlware components that are in the http request and response pipline
- Each middleware component can modify the http request and http response before passing to the next component
  - short circuit a request
  - edit the content of a request
  - generate the content for a response
  - edit the content of a reponse

Browser &gt; Request &gt; Authentication MiddleWare &gt; RoutingMiddleware &gt; Authentication Middleware &gt; Response &gt; Browser

A shortcircuited request is when a middleware throws back the request before getting through the rest, ie. validation middleware fails

Common ASP Helper Tags

```
<a asp-action="Index" asp-controller="Home">Home</a>
<label asp-for="MonthlyInvestment">Monthly Investment</label>
```

ASP Net Actions

- HttpGet
- HttpPost

Methods for returning a view from a controller

- View()
- View(model)

Example

```
using Microsoft.AspNetCore.Mvc;
using FutureValue.Models;
 
public class HomeController : Controller
{
    [HttpGet]
    public IActionResult Index()
    {
        ViewBag.FV = 0;
        return View();
    }
 
    [HttpPost]
    public IActionResult Index(FutureValueModel model)
    {
        ViewBag.FV = model.CalculateFutureValue();
        return View(model);
    }
}
```

# Exception Pages

- The exception (error) pages differ depending on whether you run the application with or without debugging
- With debugging : internal server error page
  - name and description of the exception
  - stack trace, and information about the current request: query, strings, cookies, routing data
  - it is possible to define custom error page to make the error pages more user friendly
- Without debugging: Exception Helper
  - name and description of the exception
  - indication of the place in code that caused it

# Debugger Tools

- Breakpoints
- Watching variables and expressions in the breakpoint mode
  - hover over variable
  - locals, auto, and watch windows
  - immediate window
- progressing one step at a time (single stepping)

# Working with Controllers and Routing

- Methods enable and configure routing
  - UseRouting()
  - UseEndPoints(endpoints)
  - app.MapDefaultControllerRoute();
- Default route specified in the Program.cs follows this pattern
  - <span style="font-family: Consolas; color: rgb(193, 194, 197)">"{controller=Home}/{action=Index}/{id?}"</span>
  - <span style="font-family: Consolas; color: rgb(193, 194, 197)">it is possible to add more route patterns</span>

# Custom Routes

- Objective - makes urls more user friendly
- Add routing patterns to the program class
  - start wit most specific patterns and end with least specific
- Routing patterns can mix dynamic and static data
- also you can add attributes in the controller to change routes

# Route Attributes for Action Methods

```
public class HomeController : Controller
{
    [Route("/")]
    public IActionResult Index()
    {
        return Content("Home controller, Index action");
    }
 
    [Route("About")]
    public IActionResult About()
    {
        return Content("Home controller, About action");
    }
}
```

# Map Controllers that use attribute routing

```
// map controllers that use attribute routing –
// often not necessary
app.MapControllers(); 
 
// map pattern for default route 
app.MapControllerRoute(
    name: "default",
    pattern: "{controller=Home}/{action=Index}/{id?}");
```

# Best Practices

- Keep url short and descriptive
- use keywords, not implementation details
- make urls easy to type and read
- use hyphens to seperate words
- prefer names over numbers
- create nice hierarchy
- be consistent
- avoid use of query strings if possible

# Areas

- A larger app can be divided into areas
- each area can have its own controllers and views and possibly modes and other files
- if using areas, you need to add a route with areas to the startup file
- also you need to add attributes in the controller that specify the area

# Route that works with an area

```
app.MapAreaControllerRoute(
    name: "admin",
    areaName: "Admin",
    pattern: "Admin/{controller=Home}/{action=Index}/{id?}");
 
app.MapControllerRoute(
    name: "default",
    pattern: "{controller=Home}/{action=Index}/{id?}");
```

# Home controller for admin area

```
namespace GuitarShop.Areas.Admin.Controllers
{
    [Area("Admin")]
    public class HomeController : Controller
    {
        public IActionResult Index()
        {
            return View();  // maps to /Areas/Admin/Views/Home/
                            // Index.cshtml
        }
    }
}
```

# Razor Views

- Combines HTML with C# code

Razor Block Code Example

```
@{
    //one or more c# statements
}
```

# Inline code example for Razor

```
@(cs expression)
```

# Examples of Razor Code

```
<h1>@message</h1>
<p>Customer Name: @ViewBag.CustomerName</p>
<p>2 + 2 = @(2 + 2)</p>
```

# For Loop

```
<label for="month">Month:</label>
<select name="month" id="month">
    @for (int month = 1; month <= 12; month++)
    {
        <option value="@month">@month</option>
    }
</select>
```

# If Else

```
@if (ViewBag.ProductID == 1)
{
    <p>Fender Stratocaster</p>
}
else if (ViewBag.ProductID == 2)
{
    <p>Gibson Les Paul</p>
}
else
{
    <p>Product Not Found</p>
}
```

# Switch

```
@switch (ViewBag.ProductID)
{
    case 1:
        <p>Fender Stratocaster</p>
        break;
    case 2:
        <p>Gibson Les Paul</p>
        break;
    default:
        <p>Product Not Found</p>
        break;
}
```

# Conditional

```
<a asp-controller="Product" asp-action="List" asp-route-id="All" 
    class="list-group-item 
    @(ViewBag.SelectedCategoryName == "All" ? "active" : "")">
    All
</a>
```

# Common ActionResult subtypes

- ViewResult
- RedirectResult
- RedirectToActionResult
- JsonResult
- FileResult
- StatusCodeResult
- ContentResult
- EmptyResult

# Passing Data from Controller to View

- The bulk of data should be passed through the model
- the model can be a single object of some class or a collection of objects from some class
- what if we want to pass some data in addition to the model
  - ViewBag - dynamic object
  - ViewData - a dictionary
  - TempData - a dictionary
- Dictionary is a collection of key/value pairs
- Both ViewBag and ViewData persists only until the end of the end of the current request
- TempData presists accross multiple request until its read

# Check for Null Values

```
//Value type (double)
<h4>Price: @ViewBag.Price?.ToString("c")</h4>
//Reference type (string)
<h4>Book: @ViewBag.Book?.ToUpper()</h4>
```

# Keeping Data in TempData

- Normally data stored in TempData is removed after it's read
- Two methods of TempDataDictionary Class
  - Keep(key)
  - Peek(key)
- Use Peak when you want the value to stay marked as unread
- use normal read and Keep when you want to use condition to decide whether to keep it or not
- there is an overload Keep - mark all values in TempData as unread even if theyve already been read

# Programming Tips

- Make each controller only responsible for one entity (model class)
- use ViewData instead of ViewBag when
  - key name is not a valid identifier
  - you want to call a dictionary property like count or method like clear
- use tempdata when data needs to live through other request cycles, for example with a rediect
  - an example of use for tempdata is when we want to pass a feedback message to another view
  - prg pattern - post / redirect / get