o# 6.1 Interfaces
* **interface** - an interface is not a class but a set of requirements for the classes that want to conform to the interface.
* The interface is a contract or a promise for the classes implementing it agrees to respond to.
* All methods of an interface are default **public**
* Implements keyword is you to declare that a class is using an interface
* To implement an interface, you must carry out two steps


-
* You declare that your class intends to **implement** the given interface.

```
public class RandomQuote implements SmartQuotes { ... }

```

-

* You supply definitions for all methods in the interface

```
package io.zipcoder;

public interface SmartQuotes {
     String selectRandomQuote();
}
```
-

```
package io.zipcoder;

public class RandomQuote implements SmartQuotes{
    
    /**
     *  You must provide a concrete implementation for all the public methods provided
     *  by the interface you are implementing
     */
     
    public String selectRandomQuote() {
        return "Not So Random Statement";
    }
}
```
-
* **Interface Comparable\<T\>**
  * **Java Comparable** interface is used to order the objects of user-defined class. This interface is found in the **java.lang** package and contains only one method named **compareTo(Object)**. It provides single sorting sequence only, i.e. you can sort the elements on based on single data member only. For example it may be rollno, name, age or anything else.

-

  * Classes provided will most often provide you **compareTo** method to allow them to be sorted, such as **Class String**

```
public int compareTo(String anotherString)
```

-
* For the custom classes that we create, if we intend on giving users the ability to sort them , we need to have our class implement **Comparable\<T\>** , so that sorting methods know how to evaluate them.

-
```
  public static void main(String[] args){
    Sayian[] sayians = new Sayian[3];
    
    sayians[0] = new Saiyan("Vegeta", 5000);
    sayians[1] = new Saiyan("Goku", 9000);
    sayians[2] = new Saiyan("Gohan", 3000);
    
    // There is no way for this method to know how to sort these custom objects
    // by default unless this object implements Comparable.
    // Implementing Comparable tells the sort method that these objects can respond to
    // the compartTo(T t) request.
    Arrays.sort(sayians);
    
    for (Sayian s: sayians)
      System.out.println("Name=" + s.getName() + ", order=" + s.getPowerLevel());
    
  }
```
-

```
public class Saiyan implements Comparable<Saiyan>
{
  ...
  
  public int compareTo(Saiyan other){
    return Integer.compare(powerLevel, other.powerLevel )l
  }
  ...
}
```
-
-
##6.1.2 Properties of Interface

* Interfaces are not classes, you can never instantiate an interface.
* You can not instantiate an Interface, but you can declare a variable of type interface.
  * As long as the object implements the interface, you can assign it to that reference.

-

```
package io.zipcoder.Marvel

public interface GuardianOfGalaxy {
    Double attackEnemy(Enemy enemy);
    
    String battleCry();
}
```

-

```
package io.zipcoder.Marvel

public Groot implements GuardianOfGalaxy {
  
  public Double attackEnemy(Enemy enemy){
     ...
  }
  
  public String battleCry() {
    return "I am Grooooot!";
  }

}
```
-

* You can create a reference and assign it the Type of an Interface, but you cannot create an object of that type.
* You can, however make that reference point to any object that **implements ** that interface. This is possible because of polymorphism.

-

```
package io.zipcoder.Marvel

public class Guardians {
  
  public assembleGuardians(){
    GuardianOfGalaxy rocket = new GuardianOfGalaxy(); // ERROR
    GuardianOfGalaxy groot = new Groot(); // Works Great 
  }
}
```
-
-
## Interface and Abstract Classes

* A class can only extend a single class, as there will be times when you would like to apply multiple inheritance to a class.
* This can be accomplished via **implements**.
* Interfaces are polymorphic

-

```
public abstract GuardianOfGalaxy {
    Double attackEnemy(Enemy enemy);
    
    String battleCry();
}

public abstract Avengers {
  
  void AvengersAssemble();
}
```

-
```
// an object can only extend one type
public class IronMan extends Avengers , GuardianOfGalaxy{ // Error
  ....
}
```
-
* In Java, an object can only extend from one type to keep inheritance in check and easy to manage.
* Objects can however implement as many Interfaces as they would like.

-
```
public interface GuardianOfGalaxy {
    Double attackEnemy(Enemy enemy);
    
    String battleCry();
}

public interface Avengers {
  
  void AvengersAssemble();
}

public class IronMan implements Avengers, GuardianOfGalaxy{...}

```
-

##Static Methods

* For simple implementations, or default implementations of static methods it's okay to place them inside the interface. In older versions of Java this would not be allowed.

-

```
public interface GuardianFlight {
  
  /**
   * Since this interface only has one simple method
   * there is no reason for us to create a class for this simple
   * of an implementation. We can just provide a static implementation.
   **/
   
  public static void boardFlight (GuardianOfGalaxy guardian){
    GuardianShip.boardFlight(guardian);
  }
}
```
-
-
##Default Methods

* Using the keyword **Default**, it is possible to supply default implementations for an interface that will be applied to the class.
* Programmers that want to extend the method only need to use the **@Override** command

-

```
public interface PowerUpItem {
  
  /**
   * Initially there is no item equiped to add this to a character
   * you would need to call this method to equip it
   **/
  public void equipPowerUpItem(Item item);
  
  /**
   * If there is no power item equiped this method could still 
   * be called by any class.
   **/
  default Integer usePowerUpItemInAttack(){
    return 0;
  }
}
```
-
-
##6.1.6 Resolving Default Method Conflicts
* There will be times when implementing two interfaces, they may have methods with the same name with a Default implementation.
  * If the SuperClass provides a concert implementation, the compiler will pick that execution.
  * If there is not default concert implementation in the super class, then the compiler will force you to explicitly state it:
    * Person.super.getName();

-
```
public interface Mjolnir {
  default String getNameOfWeapon() {
    return "Mjolnir";
  }
}

public interface CaptainAmericasShield {
  default String getNameOfWeapon() {
    return "Cap's Shield";
  }
}
```
-
```
public class Vision implements Mjolnir, CaptainAmericasShield {
  
  /**
   * Here we have a class that implements two interfaces with default implementations
   * the compiler has no way of implicitly who should be called
   * so we have to explicitly state it.
   **/
   
  public String getNameOfWeapon(){
    return Mjolnir.super.getNameOfWeapon() + ", " + CaptainAmericasShield.super.getNameOfWeapon();
  }
}
```

-
-

## Interfaces and Callbacks

* A callback method in Java is a method that gets called when an event occurs. Usually, you can implement that by passing an implementation of a certain interface to the system that is responsible for triggering the event E.

-
```
public class ScanForNinjas implements ActionListener {

    @Override
    public void actionPerformed(ActionEvent e) {
        System.out.println("All clear no ninjas at " + e.getWhen() + " time");
    }
}
```

-

```
public class ScanForEnemies {

    public static void main(String [] args){
        ActionListener scanForNinjas = new ScanForNinjas();
        Timer t = new Timer(1000, scanForNinjas);
        t.start();
        JOptionPane.showMessageDialog(null, "Quit program?");

       System.exit(0);
    }
}
```
-
-
##Lambda Expressions

* lambda expression - is a block of code that you can pass around so it can be executed later, once or multiple times.
* functional programming - a style of building the structure and elements of computer programs—that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data.

-

## Interface Comparator\<T\>

* Type Parameters:`T` - the type of objects that may be compared by this comparatorAll Known Implementing Classes:[Collator](https://docs.oracle.com/javase/8/docs/api/java/text/Collator.html "class in java.text"), [RuleBasedCollator](https://docs.oracle.com/javase/8/docs/api/java/text/RuleBasedCollator.html "class in java.text")
* Functional Interface:This is a functional interface and can therefore be used as the assignment target for a lambda expression or method reference.
-
```
public class SpeedComparator implements Comparator<Person> {

   public int compare(Person one, Person two){
     return one.speed() - two.speed();
   }
}

...

Arrays.sort(people, new SpeedComparator);
```

-
* There is no reason to create a class just to implement a Comparator
* We can just quickly create a Lambda Expression

-

```
public class Person {
    
    public int speed;
    
    public Person(int speed){
        this.speed = speed;    
    }
}
```
-
```
public class Race {
  
  public void runRace(){
    Person tariq = new Person(1);
    Person husainBolt = new Person(100);
    
    Person[] people = new Person[]{ tariq, husainBolt};
  
    // We can create a reference using the interface Comparator
    // Then create the impementation needed for the single method
    Comparator<Person> speedComparator = (racerOne, racerTwo) -> racerOne.speed - racerTwo.speed;
    Arrays.sort(people, speedComparator);
  }
  
}
```


