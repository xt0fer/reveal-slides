# Fundamental Programming Structures in Java

-
-

## A Simple Java Program

```
public class FirstSample {
    public static void main(String[] args) {
        System.out.println("We will not use 'Hello, World!'"); }
}
```

-

- Java is case sensitive
- Class names must begin with a letter, and after that, they can have any combination of letters and digits
- You cannot use a Java reserved word
- You need to make the  le name for the source code the same as the name of the public class
- whitespace is irrelevant to the Java compiler

-

```
public class ClassName {
    public static void main(String[] args) {
        program statements
    }
}
```

-
-

##Comments

Java has three ways of marking comments:

1. `//` for single line comment
2. ` /*` and `*/` for multiline comments
3. using a `/**` to start and a `*/` to end will be used to generate documentation automatically

-

```
/**
 * This is the first sample program in Core Java Chapter 3
 * @version 1.01 1997-03-22
 * @author Gary Cornell
 */
public class FirstSample {
    public static void main(String[] args) {
        System.out.println("We will not use 'Hello, World!'");
    }
}
```
<sub>CAUTION: `/* */` comments do not nest in Java.</sub>

-
-

##Data Types

Java is a strongly typed language and every variable must have a declared type.

-

There are eight primitive types in Java:

1. int
2. short
3. long
4. byte
5. float
6. double
7. char
8. boolean

-

###Integer Types

The integer types are for numbers without fractional parts.

| Type  | Storage requirments | Range (Inclusive)                                       |
| ----- |:------------------- | :------------------------------------------------------ |
| int   | 4 bytes             | –2,147,483,648 to 2,147,483, 647 (just over 2 billion)  |
| short | 2 bytes             | –32,768 to 32,767                                       |
| long  | 8 bytes             | –9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 |
| byte  | 1 byte              | -128 to 127                                             |

-

###Floating-Point Types

The foating-point types denote numbers with fractional parts

| Type   | Storage requirments | Range (Inclusive)                                              |
| ------ |:------------------- | :------------------------------------------------------------- |
| float  | 4 bytes             | Approximately ±3.40282347E+38F (6–7 signi cant decimal digits) |
| double | 8 bytes             | Approximately ±1.79769313486231570E+308 (15 signi cant decimal digits)|

-

###The char Type

Literal values of type char are enclosed in single quotes.

Values of type char can be expressed as hexadecimal values that run from \u0000 to \uFFFF

-

| Escape sequence | Name            | Unicode Value |
| --------------- |:----------------| :------------ |
| \b              | Backspace       | \u0008        |
| \t              | Tab             | \u0009        |
| \n              | Linefeed        | \u000a        |
| \r              | Carriage return | \u000d        |
| \\"              | Double quote    | \u0022        |
| \'              | Single quote    | \u0027        |
| \\\              | Backslash       | \u005c        |

-

###The boolean Type

The boolean type has two values, false and true.

-
-

##Variables

In Java, every variable has a type. You declare a variable by placing the type  rst, followed by the name of the variable.

```
double salary;
int vacationDays;
long earthPopulation;
boolean done;
```
The semicolon is necessary because a declaration is a complete Java statement.

-


You can declare multiple variables on a single line:

```
int i, j; // both are integers
```

-

###Initializing Variables

After you declare a variable, you must explicitly initialize it by means of an as- signment statement—you can never use the value of an uninitialized variable.

```
int vacationDays;
System.out.println(vacationDays); // ERROR--variable not initialized
```

-

```
int vacationDays;
vacationDays = 12;
```

-


You can both declare and initialize a variable on the same line. For example:

```
int vacationDays = 12;
```

-

###Constants

The keyword final indicates that you can assign to the variable once, and then its
value is set once and for all. Also known as a constant.

```
public class Constants {
    public static void main(String[] args) {
        final double CM_PER_INCH = 2.54;
        double paperWidth = 8.5;
        double paperHeight = 11; System.out.println("Paper size in centimeters: "
            + paperWidth * CM_PER_INCH + " by " + paperHeight * CM_PER_INCH);
    }
}
```

-


It is probably more common in Java to create a constant so it’s available to multiple methods inside a single class. These are usually called class constants.

```
public class Constants2 {
    public static final double CM_PER_INCH = 2.54;

    public static void main(String[] args) {
        double paperWidth = 8.5;
        double paperHeight = 11; System.out.println("Paper size in centimeters: "
            + paperWidth * CM_PER_INCH + " by " + paperHeight * CM_PER_INCH);
    }
}
```
-
-

##Operators

The usual arithmetic operators

| Operators       | Arithmetic     |
| --------------- |:---------------|
| +               | Addition       |
| -               | Subtraction    |
| *               | Multiplication |
| /               | Division       |
| %               | Modulus        |


The / operator denotes integer division if both arguments are integers, and  foatingpoint division otherwise.

-

###Mathematical Functions and Constants

The Math class contains an assortment of mathematical functions that you may occasionally need

```
double x = 4;
double y = Math.sqrt(x); System.out.println(y); // prints 2.0
```

-

```
double y = Math.pow(x, a);
```

The Math class supplies the usual trigonometric functions:

- Math.sin
- Math.cos
- Math.tan
- Math.atan
- Math.atan2

-

###Conversions between Numeric Types

19 specific conversions on primitive types are called the widening primitive conversions:

- byte to short, int, long, float, or double
- short to int, long, float, or double
- char to int, long, float, or double
- int to long, float, or double
- long to float or double
- float to double

-

A widening primitive conversion does not lose information about the overall magnitude of a numeric value.

```
int n = 123456789;
float f = n; // f is 1.23456792E8
```

-

###Casts

When two values are combined with a binary operator (such as n + f where n is an integer and f is a  oating-point value), both operands are converted to a common type before the operation is carried out.

- If either of the operands is of type double, the other one will be converted to a double.
- Otherwise, if either of the operands is of type float, the other one will be converted to a float.
- Otherwise, if either of the operands is of type long, the other one will be converted to a long.
- Otherwise, both operands will be converted to an int.

-

Conversions in which loss of infor- mation is possible are done by means of casts.

```
double x = 9.997; int nx = (int) x;
```

```
double x = 9.997;
int nx = (int) Math.round(x);
```

-

###Combining Assignment with Operators

`x+=4;` is equivalent to `x=x+4;`

-

###Increment and Decrement Operators

n++ adds 1 to the current value of the variable n, and n-- subtracts 1 from it

```
int n = 12; n++;
```

-

```
int m = 7;
int n = 7;

int a = 2 * ++m; // now a is 16, m is 8
int b = 2 * n++; // now b is 14, n is 8
```

-

###Relational and boolean Operators

To test for equality, use a
double equal sign, ==.

```
3==7 // is false.
```
Use a != for inequality.

```
3!=7 // is true.
```

-

| boolean Operators |                       |
| ----------------- |:--------------------- |
| <                 | Less than             |
| >                 | Greater than          |
| <=                | Less than or equal    |
| >=                | Greater than or equal |

-

Java uses && for the logical “and” operator and || for the logical “or” operator.

The exclamation point ! is the logical negation operator.

-

The && and || operators are evaluated in “short circuit” fashion

The second argument is not evaluated if the first argument already determines the value

`expression1 && expression2`

`x != 0 && 1 / x > x + y // no division by 0`

-

The value of expression1 || expression2 is automatically true if the  first
expression is true, without evaluating the second expression.

-

Java supports the ternary ?: operator

`condition ? expression1 : expression2`

-

```
x < y ? x : y //gives the smaller of x and y
```

-

###Bitwise Operators

& ("and") | ("or") ^ ("xor") ~ ("not")

\>> and << operators which shift a bit pattern to the right or left.

\>>> operator  lls the top bits with zero, unlike >> which extends the sign
bit into the top bits. There is no <<< operator.

-

###Parentheses and Operator Hierarchy

[Java order of operations](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/operators.html)

`a && b || c`

 means

`(a && b) || c`

Since += associates right to left, the expression

`a += b += c`

means

`a += (b += c)`

-

###Enumerated Types

You can define your own enumerated type

`enum Size { SMALL, MEDIUM, LARGE, EXTRA_LARGE };`

Now you can declare variables of this type:

`Size s = Size.MEDIUM;`

-
-

##Strings

Java does not have a built-in string type. Instead, the standard Java library contains a pre- defined class called String.

```
String e = ""; // an empty string
String greeting = "Hello";
```

-

###Substrings

You can extract a substring from a larger string with the substring method of the String class.

```
String greeting = "Hello";
String s = greeting.substring(0, 3);
```

The second parameter of substring is the  rst position that you do not want to copy.

-

###Concatenation

Use + to join (concatenate) two strings.

```
String expletive = "Expletive"; String PG13 = "deleted";
String message = expletive + PG13;
```

-

When you concatenate a string with a value that is not a string, the latter is con- verted to a string.

```
int age = 13;
String rating = "PG" + age;
```

-

```
String all = String.join(" / ", "S", "M", "L", "XL"); // all is the string "S / M / L / XL"
```

-

###Strings Are Immutable

The String class gives no methods that let you change a character in an existing string.

```
greeting = greeting.substring(0, 3) + "p!";
```

Since you cannot change the individual characters in a Java string, the documen- tation refers to the objects of the String class as immutable.

-

###Testing Strings for Equality

To test whether two strings are equal, use the equals method.

```
s.equals(t)

"Hello".equals(greeting)

"Hello".equalsIgnoreCase("hello")
```

Do not use the == operator to test whether two strings are equal

-

###Empty and Null Strings

The empty string "" is a string of length 0.

`if (str.length() == 0)`

or

`if (str.equals(""))`

-

However, a String variable can also hold a special value, called null

```
if (str == null)

if (str != null && str.length() != 0)
```
-

###The String API

-

###Reading the Online API Documentation

-

###Building Strings

Using the StringBuilder class allows you to build a string from many small pieces.

```
StringBuilder builder = new StringBuilder();

builder.append(ch); // appends a single character
builder.append(str); // appends a string

String completedString = builder.toString();
```

-
-

##Input and Output

-

###Reading Input

To read console input, you  rst construct a Scanner that is attached to System.in

```
Scanner in = new Scanner(System.in);

System.out.print("What is your name? ");
String name = in.nextLine();
```
```
String firstName = in.next(); //read a single word
```

-

```
System.out.print("How old are you? ");
int age = in.nextInt();
```

Similarly, the nextDouble method reads the next  oating-point number.

-

###Formatting Output

You can print a number x to the console with the statement System.out.print(x). That command will print x with the maximum number of nonzero digits for that type.

```
double x = 10000.0 / 3.0; System.out.print(x);
// prints 3333.3333333333335
```

That is a problem if you want to display, for example, dollars and cents.

-

```
System.out.printf("%8.2f", x); // 3333.33
```
prints x with a  eld width of 8 characters and a precision of 2 characters.

-

```
System.out.printf("Hello, %s. Next year, you'll be %d", name, age);
```
Each of the format speci ers that start with a % character is replaced with the corre- sponding argument. The conversion character that ends a format speci er indicates the type of the value to be formatted

[Conversions for printf](http://alvinalexander.com/programming/printf-format-cheat-sheet)

-

In addition, you can specify  ags that control the appearance of the formatted output.

```
System.out.printf("%,.2f", 10000.0 / 3.0); // 3,333.33
```
-

You can use the static String.format method to create a formatted string without printing it

```
String message = String.format("Hello, %s. Next year, you'll be %d", name, age);
```

[Flags for printf](http://alvinalexander.com/programming/printf-format-cheat-sheet)

-

###File Input and Output

To read from a  le, construct a Scanner object

```
Scanner in = new Scanner(Paths.get("myfile.txt"), "UTF-8");
```
If the file name contains backslashes, remember to escape each of them with an additional backslash: "c:\\mydirectory\\myfile.txt".

-

To write to a file, construct a PrintWriter object.

```
PrintWriter out = new PrintWriter("myfile.txt", "UTF-8");
```

If the  le does not exist, it is created.

-

String dir = System.getProperty("user.dir");

-
-

##Control Flow

Java, like any programming language, supports both conditional statements and loops to determine control flow

-

###Block Scope

Before learning about control structures, you need to know more about blocks.
A block or compound statement consists of a number of Java statements, surrounded by a pair of braces. Blocks de ne the scope of your variables.

Blocks can be nested

-

```
public static void main(String[] args)
{
    int n;
    ...
    {
        int k;
        ...
    } // k is only defined up to here
}
```

-

You may not declare identically named variables in two nested blocks

```
public static void main(String[] args)
{
    int n;
    ...
    {
        int k;
        int n; // Error--can't redefine n in inner block ...
    }
}
```
-

###Conditional Statements

The conditional statement in Java has the form

```
if(condition) statement
{
    statement1
    statement2
    ...
}
```

-

if/else statement

```
if (condition)
{
    statement1
}
else
{
    statement2
}
```

-

if/else if

```
if (condition)
{
    statement1
}
else (condition2)
{
    statement2
}
else
{
    statement3
}
```

-

###Loops

The while loop executes a statement (which may be a block statement) while a condition is true

```
while(condition) statement
```
The while loop will never execute if the condition is false at the outset

-

If you want to make sure a block is executed at least once, you need to move the test to the bottom, using the do/while loop.

```
do statement while (condition);
```
-

###Determinate Loops

The for loop is a general construct to support iteration controlled by a counter or similar variable that is updated after every iteration.

```
for (int i = 1; i <= 10; i++)
    System.out.println(i);
```

-

###Multiple Selections—The switch Statement

```
switch (choice)
{
    case 1:
        ...
        break;
    case 2:
        ...
        break;
    case 3:
        ...
        break;
    default:
        // bad input ...
        break;
}
```

-

A case label can be

- A constant expression of type char, byte, short, or int
- An enumerated constant
- Starting with Java SE 7, a string literal

-

###Statements That Break Control Flow

The same break statement that you use to exit a switch can also be used to break out of a loop

```
while (years <= 100) {
    balance += payment;
    double interest = balance * interestRate / 100; balance += interest;
    if (balance >= goal) break;
    years++;
}
```

-

The continue statement transfers control to the header of the innermost enclosing loop

```
Scanner in = new Scanner(System.in);
while (sum < goal)
{
    System.out.print("Enter a number: ");
    n = in.nextInt();
    if (n < 0) continue;
    sum += n; // not executed if n < 0
}
```

-

##Big Numbers

If the precision of the basic integer and  oating-point types is not suf cient, you can turn to a couple of handy classes in the java.math package: BigInteger and BigDecimal.

```
BigInteger a = BigInteger.valueOf(100);
```

-

you cannot use the familiar mathematical operators such as + and * to combine big numbers

```
BigInteger c = a.add(b); // c = a + b
BigInteger d = c.multiply(b.add(BigInteger.valueOf(2))); // d = c * (b + 2)
```

-
-

##Arrays

An array is a data structure that stores a collection of values of the same type. You access each individual value through an integer index.

-

Declare an array variable by specifying the array type—which is the element type followed by [] — and the array variable name

```
int[] a;
```

Use the new operator to create the array.

```
int[] a = new int[100];
```

-

To find the number of elements of an array, use array.length

```
for (int i = 0; i < a.length; i++)
    System.out.println(a[i]);
```

-

Once you create an array, you cannot change its size

-

###The “for each” Loop

The enhanced for loop

```
for (variable : collection) statement
```

-

```
for (int element : a) System.out.println(element);
```

###Array Initializers and Anonymous Arrays

shortcut for creating an array object and supplying initial values at the same time

```
int[] smallPrimes = { 2, 3, 5, 7, 11, 13 };
```

-

anonymous array:
```
new int[] { 17, 19, 23, 29, 31, 37 }
```

-

```
smallPrimes = new int[] { 17, 19, 23, 29, 31, 37 };
//is shorthand for
int[] anonymous = { 17, 19, 23, 29, 31, 37 }; smallPrimes = anonymous;
```

###Array Copying

You can copy one array variable into another, but then both variables refer to the same array:

```
int[] luckyNumbers = smallPrimes;
luckyNumbers[5] = 12; // now smallPrimes[5] is also 12
```

-

Figure 3.14 shows the result. If you actually want to copy all values of one array into a new array, you use the copyOf method in the Arrays class

```
int[] copiedLuckyNumbers = Arrays.copyOf(luckyNumbers, luckyNumbers.length);
```

-

###Command-Line Parameters

-

###Array Sorting

To sort an array of numbers, you can use one of the sort methods in the Arrays class:

```
int[] a = new int[10000];
...
Arrays.sort(a)
```

This method uses a tuned version of the QuickSort algorithm that is claimed to be very ef cient on most data sets.

[Arrays API](https://docs.oracle.com/javase/7/docs/api/java/util/Arrays.html)

-

###Multidimensional Arrays

Multidimensional arrays use more than one index to access array elements

Declaring a two-dimensional array in Java

```
double[][] balances;
```

-

You cannot use the array until you initialize it.

```
balances = new double[NYEARS][NRATES];
```

-

```
int[][] magicSquare =
{
    {16, 3, 2, 13},
    {5, 10, 11, 8},
    {9, 6, 7, 12},
    {4, 15, 14, 1}
};

balances[i][j]
```
