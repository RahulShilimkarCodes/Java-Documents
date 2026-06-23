# Java OOP Master Guide

# Part 9 - Object Class, equals(), hashCode(), toString(), Cloning

---

# Table of Contents

1. Introduction to Object Class
2. Why Every Java Class Extends Object
3. Important Methods of Object Class
4. equals() Method
5. == vs equals()
6. hashCode() Method
7. equals() and hashCode() Contract
8. toString() Method
9. Object Cloning
10. Cloneable Interface
11. Shallow Copy
12. Deep Copy
13. finalize() Method
14. getClass() Method
15. Object Methods in Collections
16. HashMap Internals and OOP
17. Object Class in Selenium Frameworks
18. Object Class in API Frameworks
19. Common Interview Traps
20. Top Interview Questions
21. Revision Notes
22. Final Cheat Sheet

---

# 1. Introduction to Object Class

Object class is the root class of Java.

Definition:

```text id="obj001"
Every Java class directly or indirectly
inherits from Object class.
```

---

Example:

```java id="obj002"
class Employee {

}
```

---

Actually JVM Treats It As:

```java id="obj003"
class Employee extends Object {

}
```

---

Therefore:

```text id="obj004"
Every Object Gets Object Class Methods
```

---

# 2. Why Every Java Class Extends Object

Because Java Needs Common Behavior.

Examples:

```text id="obj005"
equals()

hashCode()

toString()

getClass()

clone()
```

---

Without Object Class:

```text id="obj006"
Every Class Would Need
These Methods
```

---

Object Provides:

```text id="obj007"
Standardized Behavior
```

---

# 3. Important Methods of Object Class

Most Important Methods:

```java id="obj008"
equals()

hashCode()

toString()

clone()

getClass()

wait()

notify()

notifyAll()
```

---

Interview Favorite.

---

# 4. equals() Method

Definition:

```text id="obj009"
Used to compare object contents.
```

---

Default Behavior:

```java id="obj010"
Object obj1 =
new Object();

Object obj2 =
new Object();

System.out.println(
obj1.equals(obj2)
);
```

---

Output:

```text id="obj011"
false
```

---

Because:

```text id="obj012"
Different Memory Addresses
```

---

Custom Example:

```java id="obj013"
class Employee {

    int id;

    Employee(int id){

        this.id=id;
    }

    @Override

    public boolean equals(
        Object obj){

        Employee emp =
            (Employee)obj;

        return this.id ==
               emp.id;
    }
}
```

---

Now:

```java id="obj014"
Employee e1 =
new Employee(101);

Employee e2 =
new Employee(101);
```

---

Output:

```text id="obj015"
true
```

---

# 5. == vs equals()

Very Important Interview Question.

---

Primitive:

```java id="obj016"
int a = 10;
int b = 10;

System.out.println(a==b);
```

Output:

```text id="obj017"
true
```

---

Objects:

```java id="obj018"
String s1 =
new String("Java");

String s2 =
new String("Java");
```

---

```java id="obj019"
s1 == s2
```

Output:

```text id="obj020"
false
```

---

Because:

```text id="obj021"
Memory Addresses Compared
```

---

Using equals():

```java id="obj022"
s1.equals(s2)
```

Output:

```text id="obj023"
true
```

---

Comparison Table:

| ==                  | equals()           |
| ------------------- | ------------------ |
| Memory Reference    | Content            |
| Operator            | Method             |
| Fast                | Logical Comparison |
| Works On Primitives | Mainly Objects     |

---

# 6. hashCode() Method

Definition:

```text id="obj024"
Returns integer representation
of object's hash value.
```

---

Example:

```java id="obj025"
String name =
"Java";

System.out.println(
name.hashCode()
);
```

---

Output:

```text id="obj026"
Integer Value
```

---

Purpose:

```text id="obj027"
Fast Object Lookup
```

---

Used In:

```text id="obj028"
HashMap

HashSet

Hashtable
```

---

# 7. equals() and hashCode() Contract

Golden Rule:

```text id="obj029"
Equal Objects Must Have
Same HashCode
```

---

Example:

```java id="obj030"
e1.equals(e2)
```

Returns:

```text id="obj031"
true
```

---

Then:

```java id="obj032"
e1.hashCode()
```

and

```java id="obj033"
e2.hashCode()
```

Must Be Same.

---

Interview Favorite.

---

Incorrect Implementation Causes:

```text id="obj034"
HashMap Bugs

HashSet Duplicates

Unexpected Behavior
```

---

# 8. toString() Method

Default Implementation:

```java id="obj035"
System.out.println(obj);
```

---

Output:

```text id="obj036"
Employee@1a2b3c
```

---

Meaning:

```text id="obj037"
ClassName@HashCode
```

---

Override Example:

```java id="obj038"
@Override

public String toString(){

    return "Employee{id=101}";
}
```

---

Output:

```text id="obj039"
Employee{id=101}
```

---

Benefits:

```text id="obj040"
Readable Logs

Better Debugging
```

---

# 9. Object Cloning

Definition:

```text id="obj041"
Creating exact copy of object.
```

---

Example:

```java id="obj042"
Employee emp2 =
(Employee) emp1.clone();
```

---

Benefits:

```text id="obj043"
Avoid Recreating Object
```

---

# 10. Cloneable Interface

Required For Cloning.

Example:

```java id="obj044"
class Employee
implements Cloneable {

}
```

---

Without Cloneable:

```text id="obj045"
CloneNotSupportedException
```

---

Interview Question:

```text id="obj046"
Why Use Cloneable?
```

Answer:

```text id="obj047"
Enable Object Cloning
```

---

# 11. Shallow Copy

Copies:

```text id="obj048"
References
```

---

Example:

```java id="obj049"
Employee original;
```

---

Clone:

```java id="obj050"
Employee copy;
```

---

Both Refer:

```text id="obj051"
Same Nested Objects
```

---

Diagram:

```text id="obj052"
Original

↓

Address

↓

Same Address

↓

Clone
```

---

Problem:

```text id="obj053"
Changes Affect Both Objects
```

---

# 12. Deep Copy

Copies:

```text id="obj054"
Entire Object Graph
```

---

Each Nested Object:

```text id="obj055"
Copied Separately
```

---

Diagram:

```text id="obj056"
Original

↓

Address A

Clone

↓

Address B
```

---

Benefits:

```text id="obj057"
Fully Independent Objects
```

---

Frequently Asked In Senior Interviews.

---

# 13. finalize() Method

Definition:

```text id="obj058"
Executed Before Garbage Collection
```

---

Example:

```java id="obj059"
protected void finalize(){

}
```

---

Important:

```text id="obj060"
Deprecated In Modern Java
```

---

Do Not Use In New Projects.

---

# 14. getClass() Method

Returns:

```text id="obj061"
Runtime Class Information
```

---

Example:

```java id="obj062"
Employee emp =
new Employee();
```

---

```java id="obj063"
System.out.println(
emp.getClass()
);
```

---

Output:

```text id="obj064"
class Employee
```

---

Useful For:

```text id="obj065"
Reflection

Framework Development
```

---

# 15. Object Methods in Collections

Example:

```java id="obj066"
HashSet<Employee>
```

---

Uses:

```text id="obj067"
equals()

hashCode()
```

---

To Determine:

```text id="obj068"
Duplicate Objects
```

---

Without Proper Override:

```text id="obj069"
Duplicate Entries Possible
```

---

# 16. HashMap Internals and OOP

HashMap Uses:

```text id="obj070"
hashCode()

equals()
```

---

Flow:

```text id="obj071"
Key

↓

hashCode()

↓

Bucket

↓

equals()

↓

Find Exact Object
```

---

Interview Favorite.

---

Example:

```java id="obj072"
map.put(emp,value);
```

---

Object Methods Decide Lookup Behavior.

---

# 17. Object Class in Selenium Frameworks

Page Object Example:

```java id="obj073"
LoginPage page =
new LoginPage();
```

---

Useful Overrides:

```text id="obj074"
toString()

equals()

hashCode()
```

---

Logging Example:

```java id="obj075"
System.out.println(page);
```

---

Readable Output Helps Debugging.

---

# 18. Object Class in API Frameworks

DTO Example:

```java id="obj076"
UserDTO dto =
new UserDTO();
```

---

Override:

```java id="obj077"
equals()

hashCode()

toString()
```

---

Benefits:

```text id="obj078"
Logging

Comparison

Caching
```

---

# 19. Common Interview Traps

### Trap 1

```text id="obj079"
Does == Compare Object Content?
```

Answer:

```text id="obj080"
No
```

---

### Trap 2

```text id="obj081"
Can hashCode Be Same For Different Objects?
```

Answer:

```text id="obj082"
Yes
```

Called:

```text id="obj083"
Hash Collision
```

---

### Trap 3

```text id="obj084"
Must Equal Objects Have Same HashCode?
```

Answer:

```text id="obj085"
Yes
```

---

### Trap 4

```text id="obj086"
Can Clone Work Without Cloneable?
```

Answer:

```text id="obj087"
No
```

---

### Trap 5

```text id="obj088"
Is finalize Recommended Today?
```

Answer:

```text id="obj089"
No
```

---

# 20. Top Interview Questions

### Q1 Why Does Every Class Extend Object?

```text id="obj090"
To inherit common functionality.
```

---

### Q2 Difference Between == And equals()?

```text id="obj091"
Reference vs Content Comparison.
```

---

### Q3 Why Override hashCode()?

```text id="obj092"
To maintain collection behavior.
```

---

### Q4 What Is Object Cloning?

```text id="obj093"
Creating copy of object.
```

---

### Q5 Difference Between Shallow And Deep Copy?

```text id="obj094"
Reference Copy vs Complete Copy.
```

---

### Q6 Why Override toString()?

```text id="obj095"
Better logging and debugging.
```

---

# 21. Revision Notes

```text id="obj096"
Object Class

↓

Root Class

Important Methods

↓

equals()

hashCode()

toString()

clone()

getClass()

Collections

↓

HashMap

HashSet

Need

↓

equals()

hashCode()

Cloning

↓

Shallow Copy

Deep Copy
```

---

# 22. Final Cheat Sheet

```text id="obj097"
Object

↓

Root Of Java

==

↓

Reference Comparison

equals()

↓

Content Comparison

hashCode()

↓

Fast Lookup

toString()

↓

Readable Output

clone()

↓

Object Copy

HashMap

↓

hashCode()

↓

equals()
```

---

# Interview Takeaway

If interviewer asks:

```text id="obj098"
Why are equals() and hashCode() important?
```

Strong Answer:

```text id="obj099"
equals() determines logical equality between objects,
while hashCode() determines the bucket location in
hash-based collections such as HashMap and HashSet.

If two objects are equal according to equals(),
they must return the same hashCode. Failing to
follow this contract can cause duplicate entries,
lookup failures, and unexpected collection behavior.

In enterprise applications, properly overriding
equals() and hashCode() is critical for DTOs,
entities, caching, and collection management.
```

---

# End of OOP Part 9

## Next Part

```text id="obj100"
Part 10 → SOLID Principles for Java Developers

Topics:

✓ Single Responsibility Principle

✓ Open Closed Principle

✓ Liskov Substitution Principle

✓ Interface Segregation Principle

✓ Dependency Inversion Principle

✓ Real Framework Examples

✓ Selenium Framework Design

✓ API Framework Design

✓ Spring Design Philosophy

✓ Project-Level Architecture

✓ Interview Questions

✓ Revision Notes
```
