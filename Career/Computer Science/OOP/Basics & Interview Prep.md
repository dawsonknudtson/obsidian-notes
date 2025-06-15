
- **Encapsulation** (keeping data private in a class)
    
- **Abstraction** (exposing only what's needed)
    
- **Inheritance** (base class → derived class)
    
- **Polymorphism** (methods behave differently in derived classes)

```
public class Animal {
    public virtual void Speak() {
        Console.WriteLine("Animal speaks");
    }
}
public class Dog : Animal {
    public override void Speak() {
        Console.WriteLine("Dog barks");
    }
}

```

