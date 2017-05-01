### Generics

-

- Generics allow type flexibility in code.  
- Generic type indicated with `<T>` or `<K, V>` usually  
- Compiler replaces generic types with given type (eg: `ArrayList<String>()`)

-

##Terms

- Parameterized Type
- Generic Type
- Type Inference

-

## Examples of generic Types

- List (ArrayList, LinkedList, etc)
- Map (HashMap, TreeMap, etc)

-
### Primitive types cannot be type parameters

Example:

```Java
// This will not compile!!!!

public class Main{
  public static void main(String[] args){
    ArrayList<int> primitiveArrayList = new ArrayList<>();
  }
}
```

-
### The solution? Wrapper classes!

```Java

public class Main{
  public static void main(String[] args){
    ArrayList<Integer> pg = new ArrayList<>();
  }
}
```

-
### Primitives and autoboxing

```Java
public static void main(String[] args){
  int x, y;
  x = 5;
  ArrayList<Integer> box = new ArrayList<>();
  box.add(x);
  y = box.get(0);
  System.out.println(y);
```
