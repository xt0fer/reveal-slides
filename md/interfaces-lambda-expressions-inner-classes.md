# Interfaces, Lambda, Expressions, and Inner Classes

-
-

## Interfaces

-

### The Interface Concept

An interface is not a class but a set of requirements for the classes that want to conform to the interface.

```
public interface Comparable 
{	int compareTo(Object other); 
}
```

```
public interface Comparable<T> {int compareTo(T other); // parameter has type T }
```

-
All methods of an interface are automatically public.

Interfaces never have instance fields.

Supplying instance  elds and methods that operate on them is the job of the classes that implement the interface

-

To make a class implement an interface, you carry out two steps:1. You declare that your class intends to implement the given interface.2. You supply de nitions for all methods in the interface.

-

```
class Employee implements Comparable
```

```public int compareTo(Object otherObject)
{	Employee other = (Employee) otherObject;	return Double.compare(salary, other.salary); 
}
```

-

```
class Employee implements Comparable<Employee> 
{	public int compareTo(Employee other) 
	{		return Double.compare(salary, other.salary); 
	}	
	... 
}
```

-

[java.lang.Comparable<T>](https://docs.oracle.com/javase/8/docs/api/java/lang/Comparable.html)

[java.util.Arrays](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html)

[java.lang.Integer](https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html)

[java.lang.Double](https://docs.oracle.com/javase/8/docs/api/java/lang/Double.html)

-

### Properties of Interfaces

-

### Interfaces and Abstract Classes

-

### Static Methods

-

### Default Methods

-

### Resolving Default Method Conflicts

-
-

## Examples of Interfaces

-

### Inferfaces and Callbacks

-

### The Comparator Interface

-

### Object Cloning

-
-

## Lambda Expressions

-

### Why Lambdas?

-

### The Syntax of Lambda Expressions

-

### Functional Interfaces

-

### Method References

-

### Constructor References

-

### Variable Scope

-

### Processing Lambda Expressions

-

### More about Comparators

-
-

## Inner Classes

-

### Use of an Inner Class to Access Object State

-

### Special Syntax Rules for Inner Classes

-

### Are Inner Classes Useful? Actually Necessary? Secure?

-

### Local Inner Classes

-

### Accessing Variables from Outer Methods

-

### Anonymous Inner Classes

-

### Static Inner Classes

-
-

## Proxies

-

### When to Use Proxies

-

### Creating Proxy Objects

-

### Properties of Proxy Classes
