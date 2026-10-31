

# C# Practical Programs

## 1A. Create an MVC application to perform basic Arithmetic Operations

Model – Calculator.cs

```
using System;

namespace CalculatorMVC.Models
{
    public class Calculator
    {
        public int Num1 { get; set; }
        public int Num2 { get; set; }

        public int Add()
        {
            return Num1 + Num2;
        }

        public int Subtract()
        {
            return Num1 - Num2;
        }

        public int Multiply()
        {
            return Num1 * Num2;
        }

        public double Divide()
        {
            return Num2 != 0 ? (double)Num1 / Num2 : 0;
        }
    }
}
```

Controller – HomeController.cs

```
using Microsoft.AspNetCore.Mvc;
using CalculatorMVC.Models;

namespace CalculatorMVC.Controllers
{
    public class HomeController : Controller
    {
        public IActionResult Index()
        {
            return View();
        }

        [HttpPost]
        public IActionResult Calculate(Calculator c, string operation)
        {
            ViewBag.Result = operation switch
            {
                "Add" => c.Add(),
                "Subtract" => c.Subtract(),
                "Multiply" => c.Multiply(),
                "Divide" => c.Divide(),
                _ => "Invalid Operation"
            };

            return View("Index");
        }
    }
}
```

View – Index.cshtml

```
@{
    ViewData["Title"] = "Calculator";
}

<h2>Arithmetic Calculator</h2>

<form asp-action="Calculate" method="post">
    <input type="number" name="Num1" placeholder="First Number" required />
    <input type="number" name="Num2" placeholder="Second Number" required />

    <button name="operation" value="Add">Add</button>
    <button name="operation" value="Subtract">Subtract</button>
    <button name="operation" value="Multiply">Multiply</button>
    <button name="operation" value="Divide">Divide</button>
</form>

<h3>Result: @ViewBag.Result</h3>
```

## 1B. Print Floyd's Triangle till n rows in C\#

```
using System;

class FloydTriangle
{
    static void Main()
    {
        Console.Write("Enter number of rows: ");
        int n = Convert.ToInt32(Console.ReadLine());

        int num = 1;

        for (int i = 1; i <= n; i++)
        {
            for (int j = 1; j <= i; j++)
            {
                Console.Write(num + " ");
                num++;
            }

            Console.WriteLine();
        }
    }
}
```

Output (n = 5):

```
1
2 3
4 5 6
7 8 9 10
11 12 13 14 15
```

## 1C. Arrange names of 10 cities in sorted order

```
using System;

class CitySort
{
    static void Main()
    {
        string[] cities = new string[10];

        Console.WriteLine("Enter 10 city names:");

        for (int i = 0; i < 10; i++)
        {
            cities[i] = Console.ReadLine();
        }

        Array.Sort(cities, StringComparer.OrdinalIgnoreCase);

        Console.WriteLine("\nCities in Sorted Order:");

        foreach (string city in cities)
        {
            Console.WriteLine(city);
        }
    }
}
```

## 2. Programs demonstrating C# features

### 2(a). Function Overloading

Same function name with different parameters is called function overloading.

```
using System;

class Overloading
{
    int Add(int a, int b)
    {
        return a + b;
    }

    int Add(int a, int b, int c)
    {
        return a + b + c;
    }

    double Add(double a, double b)
    {
        return a + b;
    }

    static void Main()
    {
        Overloading obj = new Overloading();

        Console.WriteLine("Addition 1: " + obj.Add(10, 20));
        Console.WriteLine("Addition 2: " + obj.Add(10, 20, 30));
        Console.WriteLine("Addition 3: " + obj.Add(5.5, 4.5));
    }
}
```

### 2(b). Inheritance (All Types)

C# supports Single, Multilevel, Hierarchical and Multiple inheritance through interfaces.

```
using System;

// Single Inheritance
class Animal
{
    public void Eat()
    {
        Console.WriteLine("Animal eats food");
    }
}

class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine("Dog barks");
    }
}

// Multilevel Inheritance
class Puppy : Dog
{
    public void Weep()
    {
        Console.WriteLine("Puppy weeps");
    }
}

// Hierarchical Inheritance
class Cat : Animal
{
    public void Meow()
    {
        Console.WriteLine("Cat meows");
    }
}

// Multiple Inheritance using Interfaces
interface IRun
{
    void Run();
}

interface ISwim
{
    void Swim();
}

class Human : IRun, ISwim
{
    public void Run()
    {
        Console.WriteLine("Human runs");
    }

    public void Swim()
    {
        Console.WriteLine("Human swims");
    }
}

class Program
{
    static void Main()
    {
        Puppy p = new Puppy();
        p.Eat();
        p.Bark();
        p.Weep();

        Cat c = new Cat();
        c.Eat();
        c.Meow();

        Human h = new Human();
        h.Run();
        h.Swim();
    }
}
```

### 2(c). Constructor Overloading

```
using System;

class Student
{
    int id;
    string name;

    public Student()
    {
        id = 1;
        name = "Unknown";
    }

    public Student(int i)
    {
        id = i;
        name = "Student";
    }

    public Student(int i, string n)
    {
        id = i;
        name = n;
    }

    public void Display()
    {
        Console.WriteLine("ID: " + id);
        Console.WriteLine("Name: " + name);
    }

    static void Main()
    {
        Student s1 = new Student();
        Student s2 = new Student(2);
        Student s3 = new Student(3, "Rahul");

        s1.Display();
        s2.Display();
        s3.Display();
    }
}
```

### 2(d). Interfaces

An interface contains method declarations which are implemented by a class.

```
using System;

interface IShape
{
    void Area();
}

class Circle : IShape
{
    public void Area()
    {
        double r = 5;
        Console.WriteLine("Circle Area: " + (3.14 * r * r));
    }
}

class Rectangle : IShape
{
    public void Area()
    {
        int l = 10, b = 5;
        Console.WriteLine("Rectangle Area: " + (l * b));
    }
}

class Program
{
    static void Main()
    {
        Circle c = new Circle();
        Rectangle r = new Rectangle();

        c.Area();
        r.Area();
    }
}
```

### 2(e). Delegates and Events

```
using System;

class Student
{
    public delegate void Notify();
    public event Notify OnResult;

    public void Result()
    {
        Console.WriteLine("Student result is declared.");

        if (OnResult != null)
            OnResult();
    }
}

class Program
{
    static void Message()
    {
        Console.WriteLine("Congratulations! You passed.");
    }

    static void Main()
    {
        Student s = new Student();

        s.OnResult += Message;

        s.Result();
    }
}
```

### 2(f). Exception Handling

```
using System;

class ExceptionDemo
{
    static void Main()
    {
        try
        {
            Console.Write("Enter first number: ");
            int a = Convert.ToInt32(Console.ReadLine());

            Console.Write("Enter second number: ");
            int b = Convert.ToInt32(Console.ReadLine());

            int result = a / b;

            Console.WriteLine("Result: " + result);
        }
        catch (DivideByZeroException)
        {
            Console.WriteLine("Cannot divide by zero.");
        }
        catch (FormatException)
        {
            Console.WriteLine("Please enter valid numbers.");
        }
        finally
        {
            Console.WriteLine("Program completed.");
        }
    }
}
```

## 3A. Create add(), multiply(), subtract(), divide() methods and call using C# delegate

```
using System;

delegate double Calculator(double a, double b);

class Program
{
    static double Add(double a, double b)
    {
        return a + b;
    }

    static double Multiply(double a, double b)
    {
        return a * b;
    }

    static double Subtract(double a, double b)
    {
        return a - b;
    }

    static double Divide(double a, double b)
    {
        return b != 0 ? a / b : 0;
    }

    static void Main()
    {
        double x = 20, y = 10;

        Calculator c;

        c = Add;
        Console.WriteLine("Addition: " + c(x, y));

        c = Multiply;
        Console.WriteLine("Multiplication: " + c(x, y));

        c = Subtract;
        Console.WriteLine("Subtraction: " + c(x, y));

        c = Divide;
        Console.WriteLine("Division: " + c(x, y));
    }
}
```

## 3B. Write a program using Multicast Delegate

A multicast delegate can call multiple methods using a single delegate object.

```
using System;

delegate void MyDelegate();

class Program
{
    static void Message1()
    {
        Console.WriteLine("Welcome to C# Programming");
    }

    static void Message2()
    {
        Console.WriteLine("Multicast Delegate Example");
    }

    static void Message3()
    {
        Console.WriteLine("Thank You!");
    }

    static void Main()
    {
        MyDelegate d;

        d = Message1;
        d += Message2;
        d += Message3;

        d();
    }
}
```

Output:

```
Welcome to C# Programming
Multicast Delegate Example
Thank You!
```

## 3C. Create BankAccount class with AccountNumber and Balance property validation

```
using System;

class BankAccount
{
    public int AccountNumber { get; set; }

    private double balance;

    public double Balance
    {
        get
        {
            return balance;
        }

        set
        {
            if (value >= 0)
            {
                balance = value;
            }
            else
            {
                Console.WriteLine("Balance cannot be negative.");
            }
        }
    }
}

class Program
{
    static void Main()
    {
        BankAccount account = new BankAccount();

        account.AccountNumber = 101;
        account.Balance = 5000;

        Console.WriteLine("Account Number: " + account.AccountNumber);
        Console.WriteLine("Balance: " + account.Balance);

        account.Balance = -1000;

        Console.WriteLine("Updated Balance: " + account.Balance);
    }
}
```


# 1. Progressive Web Application (PWA)

## 1A. Create a College Information Portal and convert it into PWA

File 1: index.html

```
<!DOCTYPE html>
<html>
<head>
    <title>College Portal</title>
    <link rel="manifest" href="manifest.json">
    <meta name="viewport" content="width=device-width, initial-scale=1">
</head>
<body>
    <h1>ABC College</h1>
    <h3>College Information Portal</h3>

    <h2>About Us</h2>
    <p>Welcome to ABC College.</p>

    <h2>Courses</h2>
    <p>BSc IT | BCom | BSc CS</p>

    <h2>Contact</h2>
    <p>Email: abc@gmail.com</p>

    <script>
        if ("serviceWorker" in navigator) {
            navigator.serviceWorker.register("sw.js");
        }
    </script>
</body>
</html>
```

File 2: manifest.json

```
{
  "name": "ABC College Portal",
  "short_name": "College",
  "start_url": "index.html",
  "display": "standalone",
  "background_color": "#ffffff",
  "theme_color": "#0066cc"
}
```

File 3: sw\.js

```
self.addEventListener("install", event => {
    event.waitUntil(
        caches.open("college-cache").then(cache =>
            cache.addAll(["index.html", "manifest.json"])
        )
    );
});

self.addEventListener("fetch", event => {
    event.respondWith(
        caches.match(event.request).then(response =>
            response || fetch(event.request)
        )
    );
});
```

## 1B. Create a PWA with a custom offline page

File 1: index.html

```
<!DOCTYPE html>
<html>
<head>
    <title>Offline PWA</title>
</head>
<body>
    <h1>Welcome to My Website</h1>
    <script>
        navigator.serviceWorker.register("sw.js");
    </script>
</body>
</html>
```

File 2: offline.html

```
<!DOCTYPE html>
<html>
<body>
    <h1>You are Offline!</h1>
    <p>Please check your internet connection.</p>
</body>
</html>
```

File 3: sw\.js

```
self.addEventListener("install", event => {
    event.waitUntil(
        caches.open("offline-cache").then(cache =>
            cache.addAll(["index.html", "offline.html"])
        )
    );
});

self.addEventListener("fetch", event => {
    event.respondWith(
        fetch(event.request).catch(() =>
            caches.match("offline.html")
        )
    );
});
```

# 2. Offline PWA and Student Management

## 2A. Develop a PWA that works offline using Service Worker

File 1: index.html

```
<!DOCTYPE html>
<html>
<head>
    <title>Offline Application</title>
</head>
<body>
    <h1>My Offline PWA</h1>
    <p>This application works without internet.</p>

    <script>
        if ("serviceWorker" in navigator) {
            navigator.serviceWorker.register("sw.js");
        }
    </script>
</body>
</html>
```

File 2: sw\.js

```
self.addEventListener("install", event => {
    event.waitUntil(
        caches.open("my-cache").then(cache =>
            cache.add("index.html")
        )
    );
});

self.addEventListener("fetch", event => {
    event.respondWith(
        caches.match(event.request).then(cached => {
            return cached || fetch(event.request);
        })
    );
});
```

Result: The website can load its cached homepage without an internet connection.

## 2B. Create a Student Record Management PWA

This program allows users to add and display student records using Local Storage.

File: index.html

```
<!DOCTYPE html>
<html>
<head>
    <title>Student Management</title>
    <link rel="manifest" href="manifest.json">
</head>
<body>
    <h2>Student Record Management</h2>

    <input id="name" placeholder="Student Name">
    <input id="roll" placeholder="Roll Number">

    <button onclick="addStudent()">Add Student</button>

    <h3>Student Records</h3>
    <ul id="list"></ul>

    <script>
        let students = JSON.parse(localStorage.getItem("students")) || [];

        function display() {
            list.innerHTML = "";
            students.forEach(s => {
                list.innerHTML += `<li>${s.roll} - ${s.name}</li>`;
            });
        }

        function addStudent() {
            let name = document.getElementById("name").value;
            let roll = document.getElementById("roll").value;

            if (!name || !roll) {
                alert("Enter all details");
                return;
            }

            students.push({name, roll});
            localStorage.setItem("students", JSON.stringify(students));

            display();
            document.getElementById("name").value = "";
            document.getElementById("roll").value = "";
        }

        display();

        if ("serviceWorker" in navigator) {
            navigator.serviceWorker.register("sw.js");
        }
    </script>
</body>
</html>
```

File: manifest.json

```
{
    "name": "Student Management",
    "short_name": "Students",
    "start_url": "index.html",
    "display": "standalone"
}
```

File: sw\.js

```
self.addEventListener("install", event => {
    event.waitUntil(
        caches.open("student-cache").then(cache =>
            cache.addAll(["index.html", "manifest.json"])
        )
    );
});

self.addEventListener("fetch", event => {
    event.respondWith(
        caches.match(event.request).then(r =>
            r || fetch(event.request)
        )
    );
});
```

# 3. HTML and Web API

## 3A. Create an HTML page containing a link to manifest.json

File: index.html

```
<!DOCTYPE html>
<html>
<head>
    <title>My PWA</title>
    <link rel="manifest" href="manifest.json">
    <meta name="viewport" content="width=device-width, initial-scale=1">
</head>
<body>
    <h1>Welcome to My PWA</h1>
    <p>This is a Progressive Web Application.</p>

    <script>
        if ("serviceWorker" in navigator) {
            navigator.serviceWorker.register("sw.js");
        }
    </script>
</body>
</html>
```

File: manifest.json

```
{
    "name": "My Application",
    "short_name": "MyApp",
    "start_url": "index.html",
    "display": "standalone",
    "background_color": "#ffffff",
    "theme_color": "#2196f3"
}
```

## 3B. Create a simple Web API that returns Student data in JSON format

Create an ASP.NET Core Web API project.

File: Program.cs

```
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

app.MapGet("/students", () =>
{
    var students = new[]
    {
        new { Id = 1, Name = "Rahul", Course = "BSc IT" },
        new { Id = 2, Name = "Amit", Course = "BCom" },
        new { Id = 3, Name = "Priya", Course = "BSc CS" }
    };

    return Results.Ok(students);
});

app.Run();
```

Run the project and open:

```
https://localhost:PORT/students
```

Output (JSON):

```
[
  {
    "id": 1,
    "name": "Rahul",
    "course": "BSc IT"
  },
  {
    "id": 2,
    "name": "Amit",
    "course": "BCom"
  },
  {
    "id": 3,
    "name": "Priya",
    "course": "BSc CS"
  }
]
```

# 4. ASP.NET Core Web API

## 4A. Develop CRUD operations using ASP.NET Core Web API and Entity Framework Core

CRUD means Create, Read, Update and Delete.

Step 1: Install NuGet packages

```
dotnet add package Microsoft.EntityFrameworkCore
dotnet add package Microsoft.EntityFrameworkCore.InMemory
```

File 1: Student.cs

```
public class Student
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Course { get; set; }
}
```

File 2: AppDbContext.cs

```
using Microsoft.EntityFrameworkCore;

public class AppDbContext : DbContext
{
    public AppDbContext(DbContextOptions<AppDbContext> options)
        : base(options) { }

    public DbSet<Student> Students { get; set; }
}
```

File 3: Program.cs

```
using Microsoft.EntityFrameworkCore;

var builder = WebApplication.CreateBuilder(args);

builder.Services.AddDbContext<AppDbContext>(options =>
    options.UseInMemoryDatabase("CollegeDB"));

var app = builder.Build();

// CREATE
app.MapPost("/students", async (Student s, AppDbContext db) =>
{
    db.Students.Add(s);
    await db.SaveChangesAsync();
    return Results.Ok(s);
});

// READ
app.MapGet("/students", async (AppDbContext db) =>
    await db.Students.ToListAsync());

// UPDATE
app.MapPut("/students/{id}", async (int id, Student s, AppDbContext db) =>
{
    var student = await db.Students.FindAsync(id);

    if (student == null)
        return Results.NotFound();

    student.Name = s.Name;
    student.Course = s.Course;

    await db.SaveChangesAsync();
    return Results.Ok(student);
});

// DELETE
app.MapDelete("/students/{id}", async (int id, AppDbContext db) =>
{
    var student = await db.Students.FindAsync(id);

    if (student == null)
        return Results.NotFound();

    db.Students.Remove(student);
    await db.SaveChangesAsync();

    return Results.Ok("Student Deleted");
});

app.Run();
```

Test API using Postman:

| Operation | Method | URL           |
| --------- | ------ | ------------- |
| Create    | POST   | `/students`   |
| Read      | GET    | `/students`   |
| Update    | PUT    | `/students/1` |
| Delete    | DELETE | `/students/1` |

For POST and PUT, select Body → raw → JSON.

```
{
    "id": 1,
    "name": "Rahul",
    "course": "BSc IT"
}
```



CRUD Covered

&#x20;This example uses an in-memory EF Core database, so records are not permanently saved after the application stops.



## 4B. Create an API endpoint to calculate Factorial and test using Postman

File: Program.cs

```
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

app.MapGet("/factorial/{n}", (int n) =>
{
    if (n < 0 || n > 20)
        return Results.BadRequest("Enter number between 0 and 20");

    long fact = 1;

    for (int i = 1; i <= n; i++)
    {
        fact = fact * i;
    }

    return Results.Ok(new
    {
        Number = n,
        Factorial = fact
    });
});

app.Run();
```

Postman Testing:

- Method: GET
- URL: `https://localhost:PORT/factorial/5`

Output:

```
{
    "number": 5,
    "factorial": 120
}
```

# 5. Advanced PWA Applications

## 5A. Create PWA with Manifest and Implement Push Notifications

File 1: index.html

```
<!DOCTYPE html>
<html>
<head>
    <title>Notification PWA</title>
    <link rel="manifest" href="manifest.json">
</head>
<body>
    <h1>My Notification PWA</h1>

    <button onclick="notify()">Enable Notifications</button>

    <script>
        navigator.serviceWorker.register("sw.js");

        async function notify() {
            let permission = await Notification.requestPermission();

            if (permission === "granted") {
                let reg = await navigator.serviceWorker.ready;

                reg.showNotification("Welcome!", {
                    body: "PWA Notification Enabled",
                    icon: "icon.png"
                });
            }
        }
    </script>
</body>
</html>
```

File 2: manifest.json

```
{
    "name": "Notification PWA",
    "short_name": "Notify",
    "start_url": "index.html",
    "display": "standalone",
    "background_color": "#ffffff",
    "theme_color": "#2196f3",
    "icons": [
        {
            "src": "icon.png",
            "sizes": "192x192",
            "type": "image/png"
        }
    ]
}
```

File 3: sw\.js

```
self.addEventListener("install", event => {
    console.log("PWA Installed");
});

self.addEventListener("push", event => {
    let data = event.data
        ? event.data.text()
        : "You have a new notification";

    event.waitUntil(
        self.registration.showNotification("My PWA", {
            body: data,
            icon: "icon.png"
        })
    );
});
```

Note: This demonstrates local notifications and the service worker push event. Actual remote push notifications also require Push API subscription with a VAPID key and a backend server to send push messages.

## 5B. Develop an E-Commerce PWA with Product Listing and Offline Cart

File 1: index.html

```
<!DOCTYPE html>
<html>
<head>
    <title>E-Commerce PWA</title>
    <link rel="manifest" href="manifest.json">
</head>
<body>
    <h1>My Online Store</h1>

    <div id="products"></div>

    <h2>Shopping Cart</h2>
    <ul id="cart"></ul>

    <script>
        let items = [
            {name: "Mobile", price: 10000},
            {name: "Laptop", price: 40000},
            {name: "Headphones", price: 1000}
        ];

        let cart = JSON.parse(localStorage.getItem("cart")) || [];

        function showProducts() {
            products.innerHTML = "";

            items.forEach((p, i) => {
                products.innerHTML += `
                    <p>${p.name} - Rs.${p.price}
                    <button onclick="addCart(${i})">Add to Cart</button>
                    </p>`;
            });
        }

        function addCart(i) {
            cart.push(items[i]);
            localStorage.setItem("cart", JSON.stringify(cart));
            showCart();
        }

        function showCart() {
            cartElement.innerHTML = "";

            cart.forEach(p => {
                cartElement.innerHTML +=
                    `<li>${p.name} - Rs.${p.price}</li>`;
            });
        }

        let products = document.getElementById("products");
        let cartElement = document.getElementById("cart");

        showProducts();
        showCart();

        if ("serviceWorker" in navigator) {
            navigator.serviceWorker.register("sw.js");
        }
    </script>
</body>
</html>
```

File 2: manifest.json

```
{
    "name": "Online Shopping",
    "short_name": "Shop",
    "start_url": "index.html",
    "display": "standalone",
    "background_color": "#ffffff",
    "theme_color": "#2196f3"
}
```

File 3: sw\.js

```
self.addEventListener("install", event => {
    event.waitUntil(
        caches.open("shop-cache").then(cache =>
            cache.addAll(["index.html", "manifest.json"])
        )
    );
});

self.addEventListener("fetch", event => {
    event.respondWith(
        caches.match(event.request).then(response =>
            response || fetch(event.request)
        )
    );
});
```

Features:

- Displays products with prices.
- Add products to shopping cart.
- Saves cart using Local Storage.
- Cart data remains available offline.
- Service Worker caches the website.

# 

## Important practical tips

1. PWA programs: Keep `index.html`, `manifest.json` and `sw.js` in the same folder.
2. ASP.NET programs: Run using Visual Studio or `dotnet run`.
3. Postman: Use the correct HTTP method (GET, POST, PUT, DELETE).
4. Offline testing: First open the website online, let the Service Worker install, then turn off internet and refresh.
5. PWA requirement: Use `localhost` or HTTPS; opening HTML directly using `file://` will not properly register a Service Worker.


