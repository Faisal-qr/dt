DOT NET CORE & PWA | PRACTICAL EXAM GUIDE
Module 1 + Module 2 • File names, code and execution steps
DOT NET CORE & PWA — COMPLETE PRACTICAL
GUIDE
Module 1 + Module 2 | Easy code + exact file names/types + short creation and run steps. Prepared for practical
exams.
Setup: Visual Studio 2022 with ASP.NET and web development workload; .NET SDK; VS Code for HTML/PWA;
Chrome; Postman for APIs. Run PWAs on http://localhost (not file://).
MODULE 1 — C# / ASP.NET
1A — MVC basic arithmetic
Project type: ASP.NET Core Web App (Model-View-Controller)
1. Visual Studio → Create project → ASP.NET Core Web App (Model-View-Controller) → Create.
2. Controllers → Add Controller → Empty MVC Controller → CalcController.cs.
3. Views → create folder Calc → Add View Index.cshtml.
4. Run Ctrl+F5; open /Calc.
FILE: Controllers/CalcController.cs [C# / Config]
using Microsoft.AspNetCore.Mvc;
public class CalcController : Controller {
public IActionResult Index(double a=0,double b=0,string op="+") {
double result=op switch {"+"=>a+b,"-"=>a-b,"*"=>a*b,"/" when b!=0=>a/b,_=>0};
ViewBag.Result=result; return View();
}
}
FILE: Views/Calc/Index.cshtml [File]
<form>
<input type="number" name="a" step="any" required />
<select name="op"><option>+</option><option>-
</option><option>*</option><option>/</option></select>
<input type="number" name="b" step="any" required />
<button>Calculate</button></form>
<h2>Result: @ViewBag.Result</h2>
Check / Note: For division by zero, add explicit error handling in production.
1B — Floyd triangle up to n rows
Project type: C# Console App
1. Create C# Console App → open Program.cs.
2. Replace code → Ctrl+F5 → enter rows.
FILE: Program.cs [C# / Config]
Console.Write("Rows: ");
int n=int.Parse(Console.ReadLine()!);
DOT NET CORE & PWA | PRACTICAL EXAM GUIDE
Module 1 + Module 2 • File names, code and execution steps
int k=1;
for(int i=1; i<=n; i++){
for(int j=1; j<=i; j++) Console.Write(k++ + " ");
Console.WriteLine();
}
1C — Sort 10 city names
Project type: C# Console App
1. Create Console App → Program.cs.
2. Paste code → Run → type 10 cities.
FILE: Program.cs [C# / Config]
string[] cities=new string[10];
for(int i=0; i<10; i++){Console.Write($"City {i+1}: "); cities[i]=Console.ReadLine()??""; }
Array.Sort(cities,StringComparer.OrdinalIgnoreCase);
foreach(string city in cities) Console.WriteLine(city);
2 — Function Overloading
Project type: C# Console App
1. Create a new Console App for this example.
2. Replace Program.cs; run Ctrl+F5.
FILE: Program.cs [C# / Config]
class Demo { static int Add(int a,int b)=>a+b; static double Add(double a,double b)=>a+b; static
void Main(){Console.WriteLine(Add(2,3)); Console.WriteLine(Add(2.5,3.5)); }}
2 — Inheritance (single/multilevel/hierarchical)
Project type: C# Console App
1. Create a new Console App for this example.
2. Replace Program.cs; run Ctrl+F5.
FILE: Program.cs [C# / Config]
class A { public void Show()=>Console.WriteLine("A"); }
class B:A {}
class C:B {} // multilevel A -> B -> C
class D:A {} // hierarchical B and D inherit A
class Program {static void Main(){new C().Show(); new D().Show(); }}
2 — Constructor Overloading
Project type: C# Console App
1. Create a new Console App for this example.
2. Replace Program.cs; run Ctrl+F5.
FILE: Program.cs [C# / Config]
DOT NET CORE & PWA | PRACTICAL EXAM GUIDE
Module 1 + Module 2 • File names, code and execution steps
class Student {public Student(){Console.WriteLine("Default"); } public Student(string
n){Console.WriteLine(n); }}
class Program {static void Main(){new Student(); new Student("Manthan"); }}
2 — Interfaces
Project type: C# Console App
1. Create a new Console App for this example.
2. Replace Program.cs; run Ctrl+F5.
FILE: Program.cs [C# / Config]
interface IPrint {void Print(); }
class Demo:IPrint {public void Print()=>Console.WriteLine("Hello"); }
class Program {static void Main(){new Demo().Print(); }}
2 — Delegates and Events
Project type: C# Console App
1. Create a new Console App for this example.
2. Replace Program.cs; run Ctrl+F5.
FILE: Program.cs [C# / Config]
class Alarm {public event Action? Ring; public void Start()=>Ring?.Invoke(); }
class Program {static void Main(){var a=new Alarm(); a.Ring+=()=>Console.WriteLine("Alarm!");
a.Start(); }}
2 — Exception Handling
Project type: C# Console App
1. Create a new Console App for this example.
2. Replace Program.cs; run Ctrl+F5.
FILE: Program.cs [C# / Config]
try {Console.Write("Number: "); int n=int.Parse(Console.ReadLine()!); Console.WriteLine(10/n); }
catch(Exception e){Console.WriteLine(e.Message); } finally{Console.WriteLine("Done"); }
3A — Add, subtract, multiply, divide using delegate
Project type: C# Console App
1. Create Console App → Program.cs → paste and run.
FILE: Program.cs [C# / Config]
delegate double Operation(double a,double b);
class Program {
static double Add(double a,double b)=>a+b;
static double Sub(double a,double b)=>a-b;
static double Mul(double a,double b)=>a*b;
static double Div(double a,double b)=>a/b;
DOT NET CORE & PWA | PRACTICAL EXAM GUIDE
Module 1 + Module 2 • File names, code and execution steps
static void Main(){Operation op=Add; Console.WriteLine(op(8,2)); op=Sub;
Console.WriteLine(op(8,2)); op=Mul; Console.WriteLine(op(8,2)); op=Div;
Console.WriteLine(op(8,2)); }
}
3B — Multicast delegate
Project type: C# Console App
1. Create Console App → Program.cs → paste and run.
FILE: Program.cs [C# / Config]
delegate void Message();
class Program {
static void One()=>Console.WriteLine("First");
static void Two()=>Console.WriteLine("Second");
static void Main(){Message m=One; m+=Two; m(); }
}
3C — BankAccount with validated Balance
Project type: C# Console App
1. Create Console App → Program.cs → paste and run.
FILE: Program.cs [C# / Config]
class BankAccount {
public int AccountNumber {get; set; }
private decimal balance;
public decimal Balance {get=>balance; set {if(value<0)throw new ArgumentException("Negative not
allowed"); balance=value; }}
}
class Program {static void Main(){var b=new BankAccount{AccountNumber=101,Balance=500};
Console.WriteLine(b.Balance); }}
4A — Student Registration Form using Web Forms controls
Project type: ASP.NET Web Application (.NET Framework) → Web Forms
1. Use Visual Studio Windows with .NET Framework Web Forms template (NOT ASP.NET Core).
2. Add Web Form → Register.aspx → replace markup.
3. Run and open Register.aspx.
FILE: Register.aspx [File]
<%@ Page Language="C#" %>
<form id="form1" runat="server">
<asp:Label runat="server" Text="Name"/><asp:TextBox ID="txt" runat="server"/><br/>
<asp:RadioButton ID="male" GroupName="gender" Text="Male" runat="server"/>
<asp:RadioButton GroupName="gender" Text="Female" runat="server"/><br/>
<asp:DropDownList ID="course"
runat="server"><asp:ListItem>IT</asp:ListItem><asp:ListItem>CS</asp:ListItem></asp:DropDownList>
<asp:CheckBox ID="agree" Text="Agree" runat="server"/>
<asp:Calendar ID="cal" runat="server"/>
<asp:Button runat="server" Text="Submit" OnClick="Submit_Click"/>
<asp:Label ID="output" runat="server"/>
</form>
DOT NET CORE & PWA | PRACTICAL EXAM GUIDE
Module 1 + Module 2 • File names, code and execution steps
<script runat="server">
protected void Submit_Click(object sender,EventArgs e){output.Text=Server.HtmlEncode(txt.Text)+"
- "+course.SelectedValue+" - "+cal.SelectedDate.ToShortDateString();}
</script>
4B — Registration with validation controls
Project type: ASP.NET Web Application (.NET Framework) → Web Forms
1. Add Web Form → Validation.aspx.
2. Paste markup → run; try blank/invalid email.
FILE: Validation.aspx [File]
<%@ Page Language="C#" %>
<form runat="server">
Name: <asp:TextBox ID="name" runat="server"/>
<asp:RequiredFieldValidator runat="server" ControlToValidate="name" ErrorMessage="Name required"
ForeColor="Red"/><br/>
Email: <asp:TextBox ID="email" runat="server"/>
<asp:RegularExpressionValidator runat="server" ControlToValidate="email"
ValidationExpression="^[^@\s]+@[^@\s]+\.[^@\s]+$" ErrorMessage="Invalid email"
ForeColor="Red"/><br/>
<asp:Button runat="server" Text="Register"/>
</form>
Check / Note: Add RequiredFieldValidator for email too if email must not be blank.
4C — AdRotator control
Project type: ASP.NET Web Application (.NET Framework) → Web Forms
1. Add Web Form Ad.aspx.
2. Add XML file Ads.xml and two images a.jpg, b.jpg to project root.
3. Paste files → run Ad.aspx.
FILE: Ad.aspx [File]
<%@ Page Language="C#" %>
<form runat="server"><asp:AdRotator runat="server" AdvertisementFile="~/Ads.xml" /></form>
FILE: Ads.xml [File]
<Advertisements>
<Ad><ImageUrl>~/a.jpg</ImageUrl><NavigateUrl>https://example.com</NavigateUrl><AlternateText>Ad
A</AlternateText><Impressions>1</Impressions></Ad>
<Ad><ImageUrl>~/b.jpg</ImageUrl><NavigateUrl>https://example.org</NavigateUrl><AlternateText>Ad
B</AlternateText><Impressions>1</Impressions></Ad>
</Advertisements>
5A — Session and persistent cookies
Project type: ASP.NET Core Empty
1. Create ASP.NET Core Empty project.
2. Replace Program.cs → run → open /set then /read.
DOT NET CORE & PWA | PRACTICAL EXAM GUIDE
Module 1 + Module 2 • File names, code and execution steps
FILE: Program.cs [C# / Config]
var b=WebApplication.CreateBuilder(args); var app=b.Build();
app.MapGet("/set",(HttpContext c)=>{
c.Response.Cookies.Append("session","hello");
c.Response.Cookies.Append("persistent","welcome",new
CookieOptions{Expires=DateTimeOffset.UtcNow.AddDays(7)});
return "Cookies set"; });
app.MapGet("/read",(HttpContext c)=>$"Session: {c.Request.Cookies["session"]}; Persistent:
{c.Request.Cookies["persistent"]}");
app.Run();
5B — Product insert with SQL Server and EF Core
Project type: ASP.NET Core Web API
1. Create ASP.NET Core Web API project.
2. NuGet: Microsoft.EntityFrameworkCore.SqlServer and Microsoft.EntityFrameworkCore.Design (matching
.NET version).
3. Create Models/Product.cs and Data/AppDb.cs; replace Program.cs.
4. Use SQL Server LocalDB on Windows; run dotnet ef migrations add Initial and dotnet ef database update
(install dotnet-ef if needed).
5. Run API → POST /products with JSON {"name":"Pen","price":10}.
FILE: Models/Product.cs [C# / Config]
public class Product {public int Id {get;set;} public string Name {get;set;}="";public decimal Price {get;set;}}
FILE: Data/AppDb.cs [C# / Config]
using Microsoft.EntityFrameworkCore;
public class AppDb:DbContext {public AppDb(DbContextOptions<AppDb> o):base(o){}public
DbSet<Product> Products=>Set<Product>(); }
FILE: Program.cs [C# / Config]
using Microsoft.EntityFrameworkCore;
var b=WebApplication.CreateBuilder(args);
b.Services.AddDbContext<AppDb>(o=>o.UseSqlServer("Server=(localdb)\\MSSQLLocalDB;
Database=ProductsDb; Trusted_Connection=True; TrustServerCertificate=True"));
var app=b.Build();
app.MapPost("/products",async(Product p,AppDb db)=>{db.Products.Add(p); await
db.SaveChangesAsync(); return Results.Ok(p); });
app.Run();
5C — Employee CRUD using EF Core
Project type: ASP.NET Core Web API
1. Create ASP.NET Core Web API project; install EF Core SqlServer + Design.
2. Create Employee.cs and AppDb.cs below.
3. Replace Program.cs; migrations add Initial and database update.
4. Test GET/POST/PUT/DELETE with Postman.
DOT NET CORE & PWA | PRACTICAL EXAM GUIDE
Module 1 + Module 2 • File names, code and execution steps
FILE: Employee.cs [C# / Config]
public class Employee {public int Id {get;set;}public string Name {get;set;}="";}
FILE: AppDb.cs [C# / Config]
using Microsoft.EntityFrameworkCore;
public class AppDb:DbContext {public AppDb(DbContextOptions<AppDb> o):base(o){}public
DbSet<Employee> Employees=>Set<Employee>(); }
FILE: Program.cs [C# / Config]
using Microsoft.EntityFrameworkCore;
var b=WebApplication.CreateBuilder(args);
b.Services.AddDbContext<AppDb>(o=>o.UseSqlServer("Server=(localdb)\\MSSQLLocalDB;
Database=EmployeesDb; Trusted_Connection=True; TrustServerCertificate=True"));
var app=b.Build();
app.MapGet("/employees",async(AppDb db)=>await db.Employees.ToListAsync());
app.MapGet("/employees/{id}",async(int id,AppDb db)=>await db.Employees.FindAsync(id) is
Employee e?Results.Ok(e):Results.NotFound());
app.MapPost("/employees",async(Employee e,AppDb db)=>{db.Employees.Add(e); await
db.SaveChangesAsync(); return Results.Ok(e); });
app.MapPut("/employees/{id}",async(int id,Employee input,AppDb db)=>{var e=await
db.Employees.FindAsync(id); if(e==null)return Results.NotFound(); e.Name=input.Name; await
db.SaveChangesAsync(); return Results.Ok(e); });
app.MapDelete("/employees/{id}",async(int id,AppDb db)=>{var e=await db.Employees.FindAsync(id);
if(e==null)return Results.NotFound(); db.Employees.Remove(e); await db.SaveChangesAsync();
return Results.NoContent(); });
app.Run();
5D — Authentication and authorization
Project type: ASP.NET Core Empty (demo cookie authentication)
1. Create ASP.NET Core Empty project.
2. Replace Program.cs.
3. Run → /login → /private → /logout.
FILE: Program.cs [C# / Config]
using Microsoft.AspNetCore.Authentication;
using Microsoft.AspNetCore.Authentication.Cookies;
using System.Security.Claims;
var b=WebApplication.CreateBuilder(args);
b.Services.AddAuthentication(CookieAuthenticationDefaults.AuthenticationScheme).AddCookie(o=>o.L
oginPath="/login");
b.Services.AddAuthorization(); var app=b.Build(); app.UseAuthentication();
app.UseAuthorization();
app.MapGet("/login",async(HttpContext c)=>{var claims=new[]{new
Claim(ClaimTypes.Name,"Student")}; await
c.SignInAsync(CookieAuthenticationDefaults.AuthenticationScheme,new ClaimsPrincipal(new
ClaimsIdentity(claims,CookieAuthenticationDefaults.AuthenticationScheme))); return "Logged in";
});
app.MapGet("/private",(ClaimsPrincipal u)=>"Welcome "+u.Identity?.Name).RequireAuthorization();
app.MapGet("/logout",async(HttpContext c)=>{await c.SignOutAsync(); return "Logged out"; });
app.Run();
Check / Note: Exam demo only: /login has no password. Real applications must validate credentials securely.
DOT NET CORE & PWA | PRACTICAL EXAM GUIDE
Module 1 + Module 2 • File names, code and execution steps
MODULE 2 — PWA / WEB API
1A — College Information Portal PWA
Project type: HTML + manifest + service worker
1. Create folder and files listed below in VS Code.
2. Open terminal in folder → run: python -m http.server 8000 (or VS Code Live Server).
3. Open http://localhost:8000 in Chrome → F12 → Application → Service Workers / Manifest.
4. Load once online, then test Offline in DevTools Network and reload.
FILE: index.html [HTML/CSS/JS]
<!doctype html><html><head><meta name="viewport" content="width=device-width,initial-scale=1"><link
rel="manifest" href="manifest.json"></head><body><h1>College Portal</h1><p>Courses: BSc IT, BSc
CS</p><script>if("serviceWorker" in
navigator)navigator.serviceWorker.register("sw.js");</script></body></html>
FILE: manifest.json [C# / Config]
{"name":"College
Portal","short_name":"College","start_url":"./index.html","display":"standalone","icons":[{"src"
:"icon.png","sizes":"192x192","type":"image/png"}]}
FILE: sw.js [HTML/CSS/JS]
const CACHE="college-v1"; const FILES=["./","./index.html","./manifest.json","./icon.png"];
self.addEventListener("install",e=>e.waitUntil(caches.open(CACHE).then(c=>c.addAll(FILES))));
self.addEventListener("fetch",e=>e.respondWith(caches.match(e.request).then(r=>r||fetch(e.reques
t))));
Check / Note: Create a real 192×192 PNG named icon.png or remove its references before testing.
1B — Custom offline page
Project type: HTML + service worker
1. Create folder and files listed below in VS Code.
2. Open terminal in folder → run: python -m http.server 8000 (or VS Code Live Server).
3. Open http://localhost:8000 in Chrome → F12 → Application → Service Workers / Manifest.
4. Load once online, then test Offline in DevTools Network and reload.
FILE: index.html [HTML/CSS/JS]
<h1>My PWA</h1><p>Try disconnecting
internet.</p><script>navigator.serviceWorker.register("sw.js")</script>
FILE: offline.html [HTML/CSS/JS]
<h1>You are offline</h1><p>Please connect to the internet.</p>
FILE: sw.js [HTML/CSS/JS]
self.addEventListener("install",e=>e.waitUntil(caches.open("offlinev1").then(c=>c.addAll(["./index.html","./offline.html"]))));
DOT NET CORE & PWA | PRACTICAL EXAM GUIDE
Module 1 + Module 2 • File names, code and execution steps
self.addEventListener("fetch",e=>{if(e.request.mode==="navigate")e.respondWith(fetch(e.request).
catch(()=>caches.match("./offline.html"))); });
Check / Note: Visit online once; then navigate to an uncached URL while offline to see the custom page.
2A — Offline mode using Service Worker
Project type: HTML + service worker
1. Create folder and files listed below in VS Code.
2. Open terminal in folder → run: python -m http.server 8000 (or VS Code Live Server).
3. Open http://localhost:8000 in Chrome → F12 → Application → Service Workers / Manifest.
4. Load once online, then test Offline in DevTools Network and reload.
FILE: index.html [HTML/CSS/JS]
<h1>Offline Ready App</h1><p>Works after first
visit.</p><script>navigator.serviceWorker.register("sw.js")</script>
FILE: sw.js [HTML/CSS/JS]
self.addEventListener("install",e=>e.waitUntil(caches.open("appv1").then(c=>c.addAll(["./","./index.html"]))));
self.addEventListener("fetch",e=>e.respondWith(caches.match(e.request).then(r=>r||fetch(e.reques
t))));
2B — Student Record Management PWA
Project type: HTML + JS + service worker
1. Create folder and files listed below in VS Code.
2. Open terminal in folder → run: python -m http.server 8000 (or VS Code Live Server).
3. Open http://localhost:8000 in Chrome → F12 → Application → Service Workers / Manifest.
4. Load once online, then test Offline in DevTools Network and reload.
FILE: index.html [HTML/CSS/JS]
<h1>Student Records</h1><input id="name" placeholder="Student name"><button
onclick="add()">Add</button><ul id="list"></ul><script
src="app.js"></script><script>navigator.serviceWorker.register("sw.js")</script>
app.js [HTML/CSS/JS]
let students=JSON.parse(localStorage.getItem("students")||"[]");
function show(){list.innerHTML=""; students.forEach((s,i)=>{let li=document.createElement("li");
li.textContent=s+" "; let b=document.createElement("button"); b.textContent="Delete";
b.onclick=()=>{students.splice(i,1); save()}; li.append(b); list.append(li)})}
function save(){localStorage.setItem("students",JSON.stringify(students)); show()}
function add(){if(name.value.trim()){students.push(name.value.trim()); name.value="";
save()}}show();
FILE: sw.js [HTML/CSS/JS]
self.addEventListener("install",e=>e.waitUntil(caches.open("studentsv1").then(c=>c.addAll(["./","./index.html","./app.js"]))));
DOT NET CORE & PWA | PRACTICAL EXAM GUIDE
Module 1 + Module 2 • File names, code and execution steps
self.addEventListener("fetch",e=>e.respondWith(caches.match(e.request).then(r=>r||fetch(e.reques
t))));
Check / Note: localStorage stores student data offline in this browser.
3A — HTML page linked to manifest
Project type: HTML + manifest
1. Create folder and files listed below in VS Code.
2. Open terminal in folder → run: python -m http.server 8000 (or VS Code Live Server).
3. Open http://localhost:8000 in Chrome → F12 → Application → Service Workers / Manifest.
4. Load once online, then test Offline in DevTools Network and reload.
FILE: index.html [HTML/CSS/JS]
<!doctype html><html><head><link rel="manifest" href="manifest.json"></head><body><h1>Welcome to My
App</h1></body></html>
FILE: manifest.json [C# / Config]
{"name":"My
App","short_name":"App","start_url":"./index.html","display":"standalone","background_color":"#f
fffff"}
Check / Note: A manifest alone does not make the page work offline.
3B — Student JSON Web API
Project type: ASP.NET Core Empty
1. Create ASP.NET Core Empty project.
2. Replace Program.cs → Ctrl+F5 → open /students.
FILE: Program.cs [C# / Config]
var b=WebApplication.CreateBuilder(args); var app=b.Build();
var students=new[]{new{Id=1,Name="Aman"},new{Id=2,Name="Manthan"}};
app.MapGet("/students",()=>Results.Json(students));
app.Run();
4A — CRUD using ASP.NET Core API + EF Core
Project type: ASP.NET Core Web API
1. Use Module 1 practical 5C project and files.
2. Rename Employee → Student or keep Employee as the entity.
3. Run EF migrations, test GET, POST, PUT, DELETE in Postman.
Example POST body (JSON) [File]
{"name":"Aman"}
Example PUT body (JSON) [File]
{"id":1,"name":"Aman Updated"}
DOT NET CORE & PWA | PRACTICAL EXAM GUIDE
Module 1 + Module 2 • File names, code and execution steps
Check / Note: Full runnable EF Core CRUD code is given in Module 1 → 5C; same API pattern.
4B — Factorial API tested with Postman
Project type: ASP.NET Core Empty
1. Create ASP.NET Core Empty project → replace Program.cs.
2. Run → copy localhost port.
3. Postman → GET http://localhost:PORT/factorial/5 → Send.
FILE: Program.cs [C# / Config]
var b=WebApplication.CreateBuilder(args); var app=b.Build();
app.MapGet("/factorial/{n:int}",(int n)=>{
if(n<0||n>20)return Results.BadRequest("Enter 0 to 20");
long f=1; for(int i=2; i<=n; i++)f*=i;
return Results.Ok(new{Number=n,Factorial=f});
}); app.Run();
Check / Note: 5! = 120; limit 20 prevents long overflow.
5A — Manifest and push notification PWA
Project type: HTML + manifest + service worker
1. Create folder and files listed below in VS Code.
2. Open terminal in folder → run: python -m http.server 8000 (or VS Code Live Server).
3. Open http://localhost:8000 in Chrome → F12 → Application → Service Workers / Manifest.
4. Load once online, then test Offline in DevTools Network and reload.
FILE: index.html [HTML/CSS/JS]
<h1>Notification Demo</h1><button id="btn">Show
Notification</button><script>navigator.serviceWorker.register("sw.js");btn.onclick=async()=>{if(await
Notification.requestPermission()==="granted"){let r=await
navigator.serviceWorker.ready;r.showNotification("Hello!",{body:"PWA notification"})}}</script>
FILE: manifest.json [C# / Config]
{"name":"Notify
PWA","short_name":"Notify","start_url":"./index.html","display":"standalone","icons":[{"src":"ic
on.png","sizes":"192x192","type":"image/png"}]}
FILE: sw.js [HTML/CSS/JS]
self.addEventListener("install",()=>self.skipWaiting());
self.addEventListener("push",e=>{let msg=e.data?e.data.text():"New message";
e.waitUntil(self.registration.showNotification("Push received",{body:msg})); });
Check / Note: Create icon.png. Button demonstrates a local notification; real remote push additionally requires
PushManager subscription, VAPID keys, and a push server.
5B — E-commerce PWA with offline cart
Project type: HTML + JS + service worker
DOT NET CORE & PWA | PRACTICAL EXAM GUIDE
Module 1 + Module 2 • File names, code and execution steps
1. Create folder and files listed below in VS Code.
2. Open terminal in folder → run: python -m http.server 8000 (or VS Code Live Server).
3. Open http://localhost:8000 in Chrome → F12 → Application → Service Workers / Manifest.
4. Load once online, then test Offline in DevTools Network and reload.
FILE: index.html [HTML/CSS/JS]
<h1>Mini Shop</h1><button onclick="add('Pen')">Pen ₹10</button><button onclick="add('Book')">Book
₹50</button><h2>Cart</h2><ul id="cart"></ul><script
src="app.js"></script><script>navigator.serviceWorker.register("sw.js")</script>
app.js [HTML/CSS/JS]
let items=JSON.parse(localStorage.getItem("cart")||"[]");
function show(){cart.innerHTML=""; items.forEach((x,i)=>{let li=document.createElement("li");
li.textContent=x+" "; let b=document.createElement("button"); b.textContent="Remove";
b.onclick=()=>{items.splice(i,1); save()}; li.append(b); cart.append(li)})}
function save(){localStorage.setItem("cart",JSON.stringify(items)); show()}
function add(x){items.push(x); save()}show();
FILE: sw.js [HTML/CSS/JS]
self.addEventListener("install",e=>e.waitUntil(caches.open("shopv1").then(c=>c.addAll(["./","./index.html","./app.js"]))));
self.addEventListener("fetch",e=>e.respondWith(caches.match(e.request).then(r=>r||fetch(e.reques
t))));
Check / Note: Open online once; add cart items; switch offline and reload. Cart persists using localStorage.
QUICK VIVA NOTES
• MVC = Model, View, Controller; separates data, UI, and request logic.
• Delegate = type-safe reference to a method; multicast delegate calls multiple methods.
• Property = get/set access to fields; validation can prevent invalid values.
• Web Forms uses .NET Framework; ASP.NET Core uses modern MVC/Razor/API, not Web Forms.
• Entity Framework Core = ORM that maps C# objects to database tables.
• CRUD = Create, Read, Update, Delete.
• PWA = installable web app with manifest and service worker capabilities.
• Service Worker = background script that intercepts requests and enables caching.
• Manifest = JSON file describing app name, icons, start URL, display mode.
• Push notification = server-triggered notification delivered via push service; local notifications alone are
different.
