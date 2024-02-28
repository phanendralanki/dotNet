# OOPS Concepts

#### 1.Why do we need OOP?
- oop helps us to think in terms of real world objects

``` csharp
class Patient
{
	public string name {get;set;}
	public string address {get;set;}
	public Doctor doctorWhoWillTreat {get;set;}
}

class Doctor
{
	public string name {get;set;}
}

```

#### 2.what are the important pillars in OOP?
1. Abstraction : Show only what is necessary.
2. Polymorphism: Object acts differently under different conditions, An user obj can be an admin and an admin can be user.
3. Inheritance: Parent Child relationship.
4. Encapsulation: Hide complexity, which should not shown outside.

#### 3.What is a class and object?

- class is a type, blue print that contains methods,properties etc..
- object is an instance of the class to use the properties of class.

``` csharp
Employee e1 = new Employee();
Employee e2 = new Employee();
e1.name = "phani";
e2.name = "satish";
```

#### 4.Abstraction vs Encapsulation
1. Abstraction: Show only whats necessary.
2. Encapsulation: Hide Complexity.

1. abstraction: Abstraction happens during design phase
- what has to be shown public.

2. Encapsulation: During coding/Execution phase developer uses encapsulation for the implementation of abstraction.
- Encapsulation implements abstraction.

``` csharp
public class Employee
{
	public string name {get;set;}
	public string address {get;set;}
	public void Validate()
	{
	 	CheckName();
	 	CheckAddress();
	}
	private void CheckName() 
	{

	}
	private void CheckAddress()
	{
		 
	}
}
```

#### 5.Explain Inheritance

- using the properties and methods of base class in the derived class.

```csharp
public class Employee
{
	public string name {get;set;}
	public string address {get;set;}
	public void Validate()
	{
	 	CheckName();
	 	CheckAddress();
	}
	private void CheckName() 
	{

	}
	private void CheckAddress()
	{
		 
	}
}

//Manager (is a) child of Employee
public class Manager:Employee
{
	public void Management()
	{

	}
}

```

#### 6.Explain virtual keyword?
#### 7.Explain about overriding?

- virtual keyword helps us to define some logic in the parent class which can be overridden in the child class.

``` csharp
public class Employee
{
	public string name {get;set;}
	public string address {get;set;}
	public virtual void Validate()
	{
	 	CheckName();
	 	CheckAddress();
	}
	private void CheckName() 
	{

	}
	private void CheckAddress()
	{
		 
	}
}

public class Manager:Employee
{
	public void Management()
	{

	}
	public override void Validate()
	{
	   //our own logic
	}
}

```

#### 8. Explain overloading?
- Method overloading means same method names with different signature in the same class.

``` csharp
public class Hello{
	public void Management()
	{

	}
	//Method overloading
	public void Management(string name)
	{

	}
}

```

#### 9. overloading vs overriding
1. overloading: Method with same names with different signatures.
2. overriding: Using Virtual keyword and overriding in child class.

#### 10.what is polymorphism?
- Poly means many,morph means change as per situation.
- Its an ability of object to act differently under different condition.

#### 11.Can polymorphism work without inheritance?
- Not possible
- To implement polymorphism inheritance is must.

#### 12.Static vs Dynamic Polymorphism?

1. static polymorphims - Method overloading - compile time polymorphism
2. Dynamic Polymorphism - Method overriding - RunTime polymorphism

#### Why do we need Abstract classes?
- Abstract class is a half/partially defined parent class. 

``` csharp
code:

using System;

namespace AbstractionDemo
{
    
    public class Discount{
        public static void Main(string[] args)
        {
            //you can't create instance of Customer class because it is abstract class.
            Customer c = new Customer();
            c.CalculateDiscount();
        }
    }
    
    public abstract class Customer
    {
        public string name {get;set;}
        public string address {get;set;}
        public string productName {get;set;}
        public decimal productAmount {get;set;}
    
        
        public abstract decimal CalculateDiscount();
    }
    
    public class GoldCustomer:Customer
    {
        public override decimal CalculateDiscount()
        {
            return productAmount - 10;
        }
    }
    
    public class SilverCustomer:Customer
    {
        public override decimal CalculateDiscount()
        {
            return productAmount-5;
        }
    }
    
    
}

```

#### Are abstract methods virtual?
- yes
- if you define a method with a keyword virtual then you can override it in child class.
- abstract methods in abstract class are virtual.


#### Can we create a instance of Abstract classes?
- No


#### Is it compulsory to implement Abstract methods?
- It is compulsory, if you don't implement in child class that class should also be written it as abstract.


#### Why simple base class replace Abstract class?

- A simple base class can not be defined in a pure half/partial way like abstract class.

### Interface

#### How to implement multiple Inheritance?

- Use Multiple Inheritance.

- Multiple Inheritance is mostly used in versioning , like if we want create a new version with present features along with new features.

``` csharp
using System;
namespace InterfaceDemo
{
    
    public class Code{
        static void Main(string[] args)
        {
            ICustomer x = new GoldCustomer();
            x.name = "sss";
            x.productAmount = 100;
            Console.WriteLine( x.CalculateDiscount());
        }
    }
    
    public interface ICustomer
    {
        string name {get;set;}
        string address {get;set;}
        string productName {get;set;}
        decimal productAmount {get;set;}
        
        decimal CalculateDiscount();
    }
    
    public interface ICustomerWithInterest: ICustomer
    {
        decimal CalculateInterest();
    }
    
    //implementing interface
    public abstract class Customer:ICustomer,ICustomerWithInterest
    {
        public string name {get;set;}
        public string address {get;set;}
        public string productName {get;set;}
        public decimal productAmount {get;set;}
        
        public abstract decimal CalculateDiscount();
        
        public  decimal CalculateInterest(){
            return productAmount-5;
        }
        
    }
    
    public class GoldCustomer:Customer
    {
        public override decimal CalculateDiscount()
        {
            return productAmount-5;
        }
    }
}
```



#### Can we write logic in interface?
- No

#### Can we define methods as private in interface?
- all the methods of interface by default are public, if we define them as private then how we can implement logic in the class.


