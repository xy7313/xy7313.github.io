---
layout: post #post
title: Start from Java 4 #post title
categories: Java #post category, seperated by space
tags: Java #post tag, seperated by space
---


## Collections
1. from util package, an interface
2. including:
    - List
    - Set: doesn't in order, no duplicates
    - Map
    - Queue: FIFO
3. CRUD: create, retrieve, update, delete
4. Collection(class):
    - sort();
    - max();
    - min();
5. Iterator: thread safe vs. Enumeration: thread not sage
    6. Iterator: hasNext(); Next();
    ```
    Iterator iter = arrlist.iterator();
    while (iter.hasNext()) {
            System.out.println(iter.next());
    }
    //LinkedList iterator:
    ListIterator listIt = linkedl.listIterator();
    //Iterating the list in forward direction use the same function as above
    // Iterating the list in backward direction
    while(listIt.hasPrevious()){
	       System.out.println(listIt.previous());
	} 
    ```
    7. Enumeration: hasMoreElements(); nextElement()
    ```
    Enumeration<String> e = Collections.enumeration(arrayList);
	while(e.hasMoreElements())
		System.out.println(e.nextElement());
    ```
6. Initialize ArrayList:
    1. Anonymous Inner class method: `ArrayList<String> cities = new ArrayList<String>(){{add("Delhi");...}};`
    2. Collections.ncopis(): `ArrayList<Integer> intlist = new ArrayList<Integer>(Collections.nCopies(10, 5));`, we get [5, 5, 5, 5, 5, 5, 5, 5, 5, 5]
7. Loop HashMap: `for (Map.Entry me : hmap.entrySet()) {`If we want to use HashSet<self-defined object>, we need to override both hashcode() and equal(). These two method are both from java....object class.
16. hashmap:
    1. sort by key :`Map<Integer, String> map = new TreeMap<Integer, String>(hmap); ` whatever the key is, when you put them to treemap (shift all entries to treemap), your key is automatically sorted.
    2. sort by value : actually is collection, the same as collection, Integer & String can invoke Collections.sort directly; obj -- compareTo
17. duplicate:
    1. add duplicates to set, get false
    2. hashmap: value equal, fine; key-value all equal, only one entry exists
9. Sort in descending order`Collections.sort(arraylist, Collections.reverseOrder());` 
10. If the elements in Collection's subclass(Set, List...) are objects, we should override compareTo in class first, then sort.
```
class someClass{
        public int compareTo(Object compareobj) {
                /* For Ascending order*/
                return this.prop - compareobj.prop;
                /* 
                    For Descending order
                    return compareobj.prop - this.prop;
                */
        }
}
public static void main(String args[]){
        ArrayList<someClass> arraylist = new ArrayList<someClass>();
        ...//add some someClass obj
        Collections.sort(arraylist);
}
```
11. `s1 = 'a'; s2 = 'h'; s1.compareTo(s2) <=0`
12. multiple properties: 
```
Collections.sort(arraylist, className.compareOneOfProp);
class className{
    ...
        public static Comparator<className> compareOneOfProp = (o1,o2) -> {return o1.OneOfProp - o2.OneOfProp;
        public static Comparator<className> compareOfAnotherProp = (o1,o2) -> {return o1.AnotherProp - o2.AnotherProp;
```
13. swap`Collections.swap(al, 1, 4);`
14. Array to ArrayList conversion: `Collections.addAll(emptyArrayList, theArray);` or `ArrayList<String> citylist= new ArrayList<String>(Arrays.asList(citynames));`
15. vector. Contructor:
    1. new Vector(); //capacity:10-20-30
    2. new Vector(int i); //capacity: 10-20-40...(double)
    2. new Vector(int i, int i); //capacity: 10-20-40...(double)

18. Date & Calendar
```
Calender cal = Calendar.getInstance();
cal.set(2017,0,1);
//month start from 0
```
9. StringTokenizer: like split
10. Random: class, function called next.int()
<!--11. author reference to book
12. database driver
13. -->

## JDBC

## Question list
1. Difference between handling checked exceptions and handling unchecked exceptions
2. An Inner class defined within a method can access everything from outside the method but only final type of variables or objects from within the method in which it is defined.（wt??）
3. no private static?
4. only want 3 objs of a class
5. 