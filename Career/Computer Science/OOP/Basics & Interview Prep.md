
- **Encapsulation** (keeping data private in a class)
	
	definition : restricting direct access to some of an object's component's, typically by making variables and methods private and then exposing them through public methods (getters/setters). It protects the internal state and ensures data integrity. 

	Real World Example(s)

		Cannot directly change the balance of bank account. You must call a deposit() or withdraw methods(). The balance field is private

		Car Dashboard : You would not access the engine directly. You press accelerator or brake, and then internal systems(engine or breaks) react accordingly - internally encapsulated 

- **Abstraction** (exposing only what's needed)

	definition : The process of hiding complex information and details, and only showing the essential features of the object. It's like showing an interface without exposing the how. 

	Real World Example : 

	Sci-Kit Learn : Using Linear regression function / model - you sort of plug and play variables. You are not seeing or understanding things that go into Linear regression like gradient descent, loss functions, feature engineering(sometimes), optimization logic

	TV Remote : Pressing buttons like up or down without really know the complexity behind them and how they work - or the circuits inside. 

	Apple Pay : When you Tap to Pay - You don't see the NFC, Encryption, Validation (with bank), and all the complex inner logic behind it. 


- **Inheritance** (base class → derived class)

	definition : Inheritance allows a class to inherit attributes and behaviors(methods) from another class. This promotes code reuse and hierarchy. 

	Example's :

	The `Vehicle` base class might have `start()`, `stop()` methods. Both `Car` and `Bike` inherit those and may add specific features like `playMusic()` in `Car`.

	An `Employee` class has `name`, `salary`. `Manager` and `Engineer` classes inherit those and may add `assignTask()` or `writeCode()`

- **Polymorphism** (methods behave differently in derived classes)

	definition : allowing methods with the same name to behave differently depending on the object calling them. It can be compile time(method overloading) or runtime (method overriding)

	Example(s) :

	Shape class may have a method called getArea() --> Circle class may inherit the shape class and call a Override method(Java) to where the getArea in the Circle class returns pier^2 maybe even same case with rectangle class but it has same method but returns length x width instead 

	sendNotification() in a parent class that sends a message. A EmailNotification class might send an email, where as a SMSNotification sends a text - all under the same method name. 


```
public class Animal {
    public virtual void Speak() {
        Console.WriteLine("Animal speaks");
    }
}
public class Dog : Animal {
	## Same method - Difference Function 
    public override void Speak() {
        Console.WriteLine("Dog barks");
    }
}

```

- **ETL** = Extract, Transform, Load
    
    - Extract from source (CSV, API, etc.)
        
    - Transform data (cleaning, formatting)
        
    - Load into target (DB or data lake)
        
- **Data Lake** = A large storage repository that holds raw data (often cloud-based like AWS S3, Snowflake)
    

📝 **Example:**

> "In an ETL pipeline, we might extract data from an API, convert date formats and filter bad rows in Python, then load the cleaned data into a Snowflake table."


- Know how **Models**, **Views**, and **Controllers** work.
    
- Understand **Routing**, **HTTP verbs** (GET/POST), **ViewModels**, and **Data Annotations**.

- **SELECT, WHERE, JOIN, GROUP BY, ORDER BY**
    
- Writing basic queries, understanding **primary keys**, **indexes**, and **normalization**

```
SELECT Orders.OrderID, Customers.Name
FROM Orders
JOIN Customers ON Orders.CustomerID = Customers.CustomerID

```

- **Arrays, Lists**
    
- **Dictionaries / HashMaps**
    
- **Stacks / Queues**
    
- Know how to use and **loop through them**, add/remove items, etc.

## MOCK INTERVIEW QUESTIONS — PRACTICE ANSWERING

---

### 🔸 **Behavioral & Process Questions**

1. **How do you debug an issue in an app?**
    
    > "I start by reproducing the bug, then I check logs, use breakpoints to trace the flow, and isolate where it breaks. I fix the root issue and test again. If needed, I write a unit test to prevent regression."
    
2. **How do you prioritize tasks in a bug fix or development sprint?**
    
    > "I prioritize based on severity, user impact, and deadline. Critical system-breaking issues come first, followed by user experience and feature work."
    

---

### 🔸 **Technical Concept Questions**

1. **What are the four pillars of OOP?**
	    Inheritance, Encapsulation, Abstraction, Polymorphism

2. **What’s the difference between a class and an object?**
	    Class is sort of a blueprint defines structure and behavior, and an object is an instance of a class 
	    
3. **What’s the purpose of a constructor?**
	    A constructor initializes a new object. It's called automatically when an object is created. You can use it to set default values or inject dependencies.
	    
4. ==****What is the difference between an abstract class and an interface?**==
	    - An **abstract class** can have both implemented methods and abstract (unimplemented) ones. It allows shared code and state.
    
	- An **interface** only defines method signatures — no implementation or state.
	    
	- You’d use interfaces for defining contracts, and abstract classes for partial implementation sharing
- 
2. **What is normalization in databases?**
	    Removing redundant data - Splitting tables and creating out relationships with foreign keys. whole goal is to reduce bad data and make sure things are running as efficient as possible (example, large tables with lots of data are more difficult to query)
	
3. **Explain JOIN vs UNION in SQL.**
    - **JOIN** combines columns from multiple tables based on a related key (e.g., inner join, left join).
    
	- **UNION** stacks rows from two queries as long as the columns match in number and type — it’s used to combine result sets.

---

### 🔸 **.NET + Web Development Questions**

1. **Walk me through the request flow in an ASP.NET MVC app.**

	    When a user sends a request, it hits the **Controller** first. The Controller handles logic, calls the appropriate **Model** to retrieve or update data, and passes that data to a **View**. The View renders the UI and sends it back to the browser.
	
2. **What’s the difference between ViewBag and ViewData?**
	    ***ViewBag** uses dynamic properties.
    
	- **ViewData** is a dictionary with string keys.  
	    ViewBag is a bit easier to work with, but ViewData is slightly faster and more flexible for dynamic lookups
	
3. **How do you create a RESTful API endpoint in .NET?**
    Create a controller, and use tags in [httpost], [httpget] and structure routes like api/users (example)
    
4. **What are GET and POST used for?**
    Get's are used for retrieving data - so read only, and post is used to send data to the server - example you are creating a new user 
---

### 🔸 **ETL / Data Questions**

1. **How would you approach building an ETL process for user data from an API?**
    
2. **What challenges could come up with transforming raw data?**
    
3. **Why might a company use a data lake instead of a traditional database?**
    
4. **What would you do if the data pipeline broke overnight?**