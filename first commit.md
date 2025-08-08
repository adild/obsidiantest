
program - 
list in which numbers are from 1 to 50 but not in order
List.of(23,43,2,1,8,50....);
print usng java, first it should print odd number ie 1,3,5,...49
after this it should print even numbers ie 2,4,6,8....50
final output: 1,3,5,7,9.....47,49,2,4,6,8,.....50
answer:
  List<Integer> numbers2 = Arrays.asList(23,43,2,1,8,50,49,3,48);
        Map<Boolean, List<Integer>> collect11 = numbers2.stream()
                .sorted()
                .collect(Collectors.partitioningBy(e -> e % 2 == 0));
        System.out.println(collect11);

move all the zeroes to the end
List<Integer> numbers1 = Arrays.asList(0,0,23,43,0,0,2,1,8,50,49,47,48,3,4,5,6,0,7,0);
        List<Integer> collect11 = numbers1.stream()
                .collect(Collectors.partitioningBy(e -> e == 0))
                .values().stream()
                // Gets the collection of lists (values of the map)
                .flatMap(List::stream)
                // Flattens the lists into a single stream
                .collect(Collectors.toList());
        System.out.println(collect11);


theroy - 

difference between ArayList and LinkedList? Scenario in which to use ArrayList and for LinkedList?

Suppose we have ArrayList and has elements such as 1,2,3. Ho wto remove first element?
Answer: lst.remove(0);

How to remove multiple occurance of 2 in a ArrayList?
Arrays.asList(0,2,4,2,2,6,0,7,2,2,2);
Answer: The removeIf() method in Java's ArrayList class is used to remove all elements from the list that satisfy a 
given condition. This method was introduced in Java 8 and utilizes the Predicate functional interface. 
List<Integer> list = new ArrayList<>(Arrays.asList(0, 2, 4, 2, 2, 6, 0, 7, 2, 2, 2));
        list.removeIf(e -> e == 2);
        System.out.println(list);

what you know hashmap?

lets say u have put all values in same hash bucket. What is the underline data structure it used? 
After java 8 what has changed? Default it will be linkedList but after java8 if more elements gets added in the bucket
then internally it converts to which data structure?
Answer: Red black tree.
Explanation: In Java's `HashMap` implementation (specifically from Java 8 onwards), 
Red-Black Trees are utilized to optimize performance in cases of high hash collisions.

How Red-Black Trees are used in `HashMap`:
- **Buckets and Linked Lists:**
    A `HashMap` fundamentally uses an array of "buckets" to store key-value pairs. Each bucket initially holds 
    a linked list to handle collisions (multiple keys hashing to the same bucket).
- **Treeification Threshold:**
    If the number of entries in a single linked list within a bucket exceeds a certain threshold 
    (known as `TREEIFY_THRESHOLD`, typically 8), the `HashMap` converts that linked list into a Red-Black Tree. 
- **Performance Improvement:**
    This conversion improves the worst-case time complexity for operations like searching, insertion, and 
    deletion within that specific bucket from O(n) (linear search in a linked list) to O(log n) 
    (logarithmic time in a balanced binary search tree). 
- **Untreeification Threshold:**
    Conversely, if the number of entries in a treeified bucket falls below a certain threshold (`UNTREEIFY_THRESHOLD`, 
    typically 6), the Red-Black Tree is converted back into a linked list. This is done to avoid the overhead of 
    tree operations when the number of elements is small.
    
Purpose: The primary purpose of using Red-Black Trees in `HashMap` is to mitigate the performance degradation that 
can occur when many keys hash to the same bucket, leading to long linked lists and inefficient operations. 
By converting these long lists into self-balancing Red-Black Trees, the `HashMap` maintains efficient 
performance even under high collision scenarios.


Tell me the drawbacks of HashMap?
what is Synchorized Hashmap?
Difference between concurrrent hashMap and Synchorized Hashmap?
tell me the feature intruduced for garbage collection regarding memory, there is some enhancement done regarding memory
in java 8?
Anwer: Java 8 introduced a significant change to memory management related to garbage collection by replacing the 
Permanent Generation (PermGen) with Metaspace. Metaspace is a native memory area that dynamically adjusts its size, 
unlike PermGen which had a fixed size and could lead to OutOfMemoryErrors if it ran out of space. 
This change provides more flexibility and reduces the likelihood of memory-related errors. 

you know about SOLID principles? What L statnd for ie Liskav substitituon principle?
what are the design principles you are aware of ?
what Singleton pattern is and how it is usefull?
refer Obsidian for explanation
