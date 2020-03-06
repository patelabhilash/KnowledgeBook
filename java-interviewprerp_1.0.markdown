## java 8 features:
Functional Interfaces (to achieve functional programming approach)  

lambda expression(provides implementation of functional interface)
forEach() method in Iterable interface.
method reference operator
stream
java nio
Base64  encoder decoder
#### method reference operator ::

it is an easy form  of lambda expression
4 ways:
Reference to a static method
Reference to an instance method of a particular object
Reference to an instance method of an arbitrary object of a particular type
Reference to a constructor

limitation : referenced method must pass same parameters as methods it is being called.

e.g.1.
```
List<Integer> numbers = Arrays.asList(5, 3, 50, 24, 40, 2, 9, 18);

numbers.stream().sorted(Integer::compareTo);
numbers.forEach(StringUtils::capitalize);
bikelist.stream().sorted(bikeFrameSizeComparator::compare);

Comparator.comparing(Employee::getName)
            .thenComparing(Employee::getDob)
            .thenComparing(Employee::getId).reversed();
// returns Compartor
```
to be used in Arrays.sort, Collections.sort


e.g.2.
```
List<String> bikeBrands = Arrays.asList("Giant", "Scott", "Trek", "GT");

public Bicycle(String brand) {
    this.brand = brand;
    this.frameSize = 0;
}

bikeBrands.stream()
  .map(Bicycle::new)
  .toArray(Bicycle[]::new);
```

Q. ConcurrentHashMap 

// I think stream adds mutability

##### Base64
```
Base64.getEncoder().encode()
Base64.getDecoder().decode(str)

Base64.getMimeEncoder().encodeToString(message.getBytes());
Base64.getMimeDecoder().decode(eStr)
```
#### FunctionalInterface
@FunctionalInterface on interface
only one abstract method

#### Lambda Expression
//without lambda, implementation is done using anonymous class

e.g.
```
@FunctionalInterface  //It is optional  
interface Drawable{  
    public void draw();  
} 
```
```
 Drawable d2=()->{  
            System.out.println("Drawing "+width);  
        };
 d2.draw();  
```
#### Anonymous Inner Class
Object created using implementing interface in a class


#### Collections
https://media.geeksforgeeks.org/wp-content/uploads/java-collection.jpg

 collection framework consists of four core interface such as Collection, List, Set, Map, and two specialized interfaces named SortedSet and SortedMap for sorting.

https://www.scientecheasy.com/2018/09/collection-hierarchy-in-java.html
https://www.geeksforgeeks.org/collections-in-java-2/

**Iterator** interface provides the facility of iterating the elements in a forward direction only.

Iterator has three methods:
 hasNext(), next(), remove(), forEachRemaining()

The **Iterable** interface is the root interface for all the collection classes.
Iterator<T> iterator()

If the underlying collection is modified while the iteration is in progress in any way other than by calling remove() method, iterator will throw an **ConcurrentModificationException**.

Java **ListIterator** interface is bi-directional iterator which is used to iterate over the elements of **list** only in either direction previous or next.

PriorityQueue, TreeSet (of SortedSet), TreeMap(of SortedMap) => maintains natural order
Linked => maintains insertion order
 Hashtable is synchronized.
Blocking => Thread safe

The “blocking” part of the name is added to imply the thread will block waiting until there’s an item available on the queue.

PriorityBlockingQueue => naturalOrder
ArrayBlockingQueue => of fixed size


concurrent == **ArrayBlockingQueue** **LinkedBlockingQueue** 
**ArrayBlockingQueue** is backed by an array that size will never change after creation. Setting the capacity to Integer.MAX_VALUE would create a big array with high costs in space. ArrayBlockingQueue is always bounded.

**LinkedBlockingQueue** creates nodes dynamically until the capacity is reached. This is by default Integer.MAX_VALUE. Using such a big capacity has no extra costs in space. LinkedBlockingQueue is optionally bounded.

Difference : when you use BlockingQueue, you can only put element into queue (and block if queue is full). With TransferQueue, you can also block until other thread receives your element (you must use new transfer method for that).

Java **CopyOnWriteArrayList** is a thread-safe variant of ArrayList in which all mutative operations (add, set, and so on) are implemented by making a fresh copy of the underlying array.

CopyOnWriteArraySet is a thread-safe variant of HashSet which uses a underlying CopyOnWriteArrayList for all of its operations.

#### Immutable class
1. no setter
2. all fields final and private
3. declare class as final

#### Wrapper Class
1.Generics in Java works only with object and does not support primitive types. hence, wrapper class
2. wrapper class extends serializable
3. Primitives can not have null

We have 8 primitive data types.
**Autoboxing** is the automatic conversion of the primitive types into their corresponding object wrapper classes. 
```
 integerList.add(Integer.valueOf(i));		//autoboxing
 ```
**Unboxing** happens when the conversion happens from wrapper class to its corresponding primitive type.
e.g.
```
for (Integer i: integerList) {
        if (i % 2 == 0)
            sum += i;           //Integer to int
    }
```

#### OOPS
https://www.scientecheasy.com/2020/02/oops-concepts-in-java.html

