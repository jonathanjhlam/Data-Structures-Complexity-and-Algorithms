# Data Structures Complexity and Algorithms
Notes for Unit: 03 - Algorithms & Data Structures.      

**Lesson Link:** [https://mrparkonline.github.io/courses/datastruct/](url)

**Data Structures:** The Data Structures course focuses on expanding our basic python skills and learning how to represent data better. These skills are crucial for all programmers as they make their leap from beginner to intermediate programmers.

# Lesson 1: Matrices & List Comprehension
## **Matrices in Python 3**

### **What is a Matrix?**
- Mathematically, matrix is a representations of numbers, symbols, or expressions in a 2-Dimensional Array.
- In Computer Science, especially with Python, we can start to create a data structure that has values in rows and columns (like a table), by utilizing a list within a list
  - There are external libraries/modules that can be imported into your python program to help this process; however, we will be constructing them with just the standalone python version
- This is a fundamental concept in mathematics especially for Calculus, Vectors, and Linear Algebra     

### **Mathematical Matrix Diagram**   
- This is a mathematical notation of what a matrix looks like:        
![image](https://user-images.githubusercontent.com/129129808/231507778-ae0ec3ce-e62b-4a30-87a3-0cfc0d86d948.png)
- Explaination:
```
  Let A represent the matrix
Matrix A has m rows and n columns ... in this case 2 rows and 4 columns.

Row 1 has values of 1 2 3 4
Column 2 has values of 2 6
```
### **Matrix A in Python 3**
```
# Python 3 Representation of matrix A

matrix_A = [
    [1, 2, 3, 4],
    [5, 6, 7, 8]
]

# Accessing Matrix A
print('Row 1: %s' % matrix_A[0]) # Recall: Indexing starts at zero in Python
print('Value at Row 2 Column 2: %s' % matrix_A[1][1])
```
- Row 1: [1, 2, 3, 4]
- Value at Row 2 Column 2: 6
  - **In Python 3, there is no data structure called a "Matrix"**

Therefore, we are programming a list within a list and following the rules of a regular matrix:
- All rows must have the same number of values
- All columns must have the same number of values
- All items in the 2D List must have the same data types
- Since indexing always starts at 0 ... row 1 is technically located at matrix_A[0]

## **List Comprehension in Python 3**
- List Comprehension is a concise method to create list in Python 3
- This technique is commonly used when:
  - The list is a result of some operations applied to all its items
  - It is a made from another sequence/iterable data
  - The list is member of another list/sequence/iterable data that satisfies a certain condition
- This is where the **lambda function** would be used, but we will learn the other way for readability
  - We will definitely talk about lambda functions in our Functional Programming Unit

### **List Comprehension Example 1**
- We are to create a list which squares all the numbers from [0,10)
```
# Old Method
squares = []
for i in range(10):
    squares.append(i ** 2)

print('Our result: %s' % squares)
```
Our result: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```
# List Comprehension

squares = [i**2 for i in range(10)]

print('Our new result: %s' % squares)
```
Our new result: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

#### **How Does it Work?**
- List comprehension consists of:
  - A **Square Bracket** containing an expression that describes the list
  - One or more **For clause** to explain its members
  - Then a zero or more **if clauses** depending on the complexity of the list
```
Examine: [i**2 for i in range(10)]

-- i**2 for i in range(10) --> is the expression that describe the list
-- i**2 describes each item in the list
-- i is taken from the for clause
-- for i in range(10) describes where i comes from
```
### **List Comprehension Example 2** 

Create the list: [[1, 3], [1, 4], [2, 3], [2, 1], [2, 4], [3, 1], [3, 4]]
From
A = [1,2,3]
B = [3,1,4]

By using list comprehension
```
# Solution
a = [1,2,3]
b = [3,1,4]

result = [[x, y] for x in a for y in b if x != y]
print(result)
```
[[1, 3], [1, 4], [2, 3], [2, 1], [2, 4], [3, 1], [3, 4]]

**Explanation:**
- Each item of our list has to be a list of two values; therefore, each item is described as [x, y]
- There are two for clauses because we are create a list from two sources.         
  -- x comes from a       
  -- y comes from b
- There is a condition to our item --> x != y         
-- Therefore, as long as the condition x != y is true, we will add the item described as [x,y] to our resulting list

### **List Comprehension Example 3**        
Use list comprehension to turn a 2D array called vec to a single list

vec = [[1,2,3], [4,5,6], [7,8,9]]      
Output: [1, 2, 3, 4, 5, 6, 7, 8, 9]

```
# Solution

vec = [[1,2,3], [4,5,6], [7,8,9]]

result = [value for row in vec for value in row]
print('Vec as a single list of values: %s' % result)
```
Vec as a single list of values: [1, 2, 3, 4, 5, 6, 7, 8, 9]

**Explanation:**
- Vec is an example of a matrix in Python 3 by using list of lists
- To grab each value one by one from the rows we must do the following in order:
  - 1. Explain what each item in the list comprehension is going to be ... in our case --> "value"
  - 2. To now access where value is, define where it comes from ... in our case --> "row";
        therefore, for row in vec
  - 3. Finally we construct our last for clause to denote that value comes from the row
- **With list comprehension, the order of your for clauses matter!**

# Lesson 2: Map & Filter
## Map & Filter In Python 3
Note: The two functions that we learn will also be revisited when we do functional programming and lambda functions

### The Map Function
The idea of a map function is to apply a function to an iterable data
```
Formatting:

map(function_name, sequence)

-- function_name: any function (built-in or selfmade) that returns a desired value of choice
-- sequence: any iterable data type
```
```
# Example
def square(num):
    ''' squares the given num argument '''
    return num ** 2
# end of square

array = list(range(1,11))
square_array = list(map(square, array))

print('Original Array:', array)
print('Array Squared:', square_array)
```
Original Array: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]        
Array Squared: [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

NOTE: the map function doesn’t return a specific data type, but rather, an python iterable data
  - Therefore, after we apply the map function, we just execute a list function on it

```
# Example 2

def upper(x):
    ''' upper() turns string x into its uppercased counter part '''
    return x.upper()

word = 'hello world!'
upper_word = ''.join(list(map(upper, word)))

print(word)
print(upper_word)

# simpler way:
print(word.upper())
```
hello world!       
HELLO WORLD!         
HELLO WORLD!

**Example 2 Explaination:**
- In example 2, we are doing a lot of unnecessary work to make our original word variable uppercased
  - This is an example of how you shouldn’t use map() for every little changes you want to a string
- It also applies to all data structure that has methods
  - Don’t want to use methods with map since there is a high probablity that there is already method for what you might want to do

## Filter Function
The idea of the filter function is to filter out items from a data set that meets a certain condition

```
Formatting:

filter(bool_returning_function, sequence)

-- function: The function name we provide for filter() must be return a boolean value ... should also be able handle 
the items inside the sequence as its arguments
-- sequence: any iterable data type
```
```
# Example 3

def isOdd(x):
    ''' isOdd() returns True if x is odd.'''
    return x % 2 != 0

array = list(range(1,101))
odds = list(filter(isOdd, array))

print('Odd Numbers from 1 to 100:', odds)
```
Odd Numbers from 1 to 100: [1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21, 23, 25, 27, 29, 31, 33, 35, 37, 39, 41, 43, 45, 47, 49, 51, 53, 55, 57, 59, 61, 63, 65, 67, 69, 71, 73, 75, 77, 79, 81, 83, 85, 87, 89, 91, 93, 95, 97, 99]

It is true that this can be done differently, but this was a simplistic use of filter to show we can filter out variables that satisfies condition… aka the condition is **True**.

## Example Problem: List of Palindromic Numbers
Our goal in this example program is to create a list of palindromic numbers (numbers that are palindromes) from 1 to 10,000.
```
# Palindromic Numbers from 1 to 10000

def isPalindrome(x):
    ''' isPalindrome returns True if string X is a palindrome.'''
    return x == x[::-1]

array = list(range(1,10000))

palindromic_numbers = list(map(int, filter(isPalindrome, map(str, array))))
print('Palindromic Numbers from 1 to 10,000', palindromicNumbers)
```
**Explanation:**
- Function Composition Breakdown
  - 1. string version of the array --> map(str, array)
  - 2. filter out the palindrome --> filter(isPalindrome, string version of the array)
  - 3. remap all values back to integers --> map(int, palindromes)
  - 4. turn the mapped integers iterable back inside a list --> list(palindromicIterables)
```
How it would looked with multiple defined variables:

array = list(range(1,10000))
str_array = map(str, array)
palindromes = filter(isPalindrome, str_array)
palindromics = map(int, palindromes)

palindromic_numbers = list(palindromes)
```
- **Composition of Functions:** Composition of Functions is the idea of using functions within a function call or apply one function to the result of another function.

# Lesson 3: Tuples
## Tuples in Python 3

### What are Tuples?
- Strings and Lists are basic iterable data types that are very similar with key differences:
  - Strings only allow alphanumeric characters and special symbols to represent text
  - Lists allow all data types as its items/members
  - Strings are immutable whereas Lists are mutable
- These significant differences cause a headache when you require the following data structure:
  - It must be immutable
  - It must allow different datatypes as items
  - It must be iterable
  - It must be nestable 
    - like a list within a list
- **All of these are solved** with a data structure called: **Tuple**

### How to use Tuples in Python 3
- Tuples are declared with parenthesis -> ()
- () is an empty tuple
- (50,) is a singleton tuple; the comma is required
- Tuples are sliceable; therefore, indexable using square brackets
- A singleton is an iterable data structure with only single item

### Tuple Example 1
```
tup = ('C', ' Java', 'Python')
empty_tup = ()
single_tup = ('Park',)

print(tup)
print(empty_tup)
print(single_tup)
```
```
('C', ' Java', 'Python')
()
('Park',)
```

### Tuple Operators
```
# Concatenation: Joining two tuples
a = (1,2,3)
b = (4,5,6)
concat_result = a + b
print('a+b:', concat_result)


# Repetition: Repeating a list multiple times
c = ('Hi!',)
repet_result = c * 3
print('c*3', repet_result)

# Membership: Check if a value exists in a tuple
d = a + b + c
print('d:', d)
print('\'Hi!\' in d:', 'Hi!' in d)
print('7 in d:', 7 in d)
```
```
a+b: (1, 2, 3, 4, 5, 6)
c*3 ('Hi!', 'Hi!', 'Hi!')
d: (1, 2, 3, 4, 5, 6, 'Hi!')
'Hi!' in d: True
7 in d: False
```

### Tuples are Iterable, Indexable, and Sliceable
```
# Iteration
example = ('C', 'Java', 'Python', 'C#', 'JavaScript')

print('Tuple example items:')
for language in example:
    print(language)
print('--')

# Indexing
print('Index 1:', example[1])
print('Last Value:', example[-1])

# Slicing
print('Backwards:', example[::-1])
print('Every other:', example[::2])
print('From 1 to end:', example[1:])
print('From 1 to 3:', example[1:3])
```
```
Tuple example items:
C
Java
Python
C#
JavaScript
--
Index 1: Java
Last Value: JavaScript
Backwards: ('JavaScript', 'C#', 'Python', 'Java', 'C')
Every other: ('C', 'Python', 'JavaScript')
From 1 to end: ('Java', 'Python', 'C#', 'JavaScript')
From 1 to 3: ('Java', 'Python')
```

### Built-in Functions with Tuple
```
example = ('C', 'Java', 'Python', 'C#', 'JavaScript')

print('Length:', len(example))
print('Minimum value:', min(example))
print('Maximum value:', max(example))
print('--')

word = 'Hello'
array = [1,2,3,4]
array_array = [[1],[2,3],[4]]

print('String to Tuple:', tuple(word))
print('List to Tuple:', tuple(array))
print('2D array to Tuple:', tuple(array_array))
print('--')

array_array[0][0] = 'p'
print(array_array)

# Note: don't have mutable data type as items in a tuple ...
```
```
Length: 5
Minimum value: C
Maximum value: Python
--
String to Tuple: ('H', 'e', 'l', 'l', 'o')
List to Tuple: (1, 2, 3, 4)
2D array to Tuple: ([1], [2, 3], [4])
--
[['p'], [2, 3], [4]]
```

### Tuple Comprehension
```
# Tuple of Even values from 1 to 100
even_tup = tuple(i for i in range(1,101) if i % 2 == 0)

print(even_tup)
```
- The parentheses were taken for a different functionality in python; therefore, we have to do comprehension like this
- The general format is the exactly the same as list comprehension

### Tuple & Python: Packing and Unpacking
```
# Examine the following code

# Packing
var_1 = 2
var_2 = 3
var_3 = 5

prime = var_1, var_2, var_3

print('Packed prime values:', prime)

# Unpacking and Repacking
fib = (0, 1, 1, 2, 3, 5, 8)

fib_0, fib_1, fib_n = fib[0], fib[1], fib[2:]
print('fib_0:', fib_0)
print('fib_1:', fib_1)
print('fib_n:', fib_n)
```
```
Packed prime values: (2, 3, 5)
fib_0: 0
fib_1: 1
fib_n: (1, 2, 3, 5, 8)
```
**Explanation:**
- Packing collect multiple variable’s values and assign it to a single variable
- Unpacking help us assign certain values from a tuple to different variables
- This becomes very useful skill when combined with variable arguments for Function Definition and Function Calls

# Lesson 4: Sets
## Sets in Python 3
- A set is an unordered collection with no duplicate elements in Python 3
- Set is a mathematical way to describe collection of different unique objects
- By following the operations and characteristics of the mathematical set, we can utilizie such data structure in our Python code

### Using Sets in Python 3
#### How to Define a Set
```
# Set definition examples:
example_set1 = {1, 2, 3}
example_set2 = {'h','e','l','l','o'}

print('example_set1:', example_set1)
print('example_set2:', example_set2) # Notice there is only 1 'l'; Also notice the order of the values outputted
print('--')

singleton_set = {7}
empty_set = set() # this is because {} is reversed for a different feature in python 3.

print('Singleton:', singleton_set)
print('Empty Set:', empty_set)
```
```
example_set1: {1, 2, 3}
example_set2: {'o', 'e', 'h', 'l'}
--
Singleton: {7}
Empty Set: set()
```
#### Basic Built-in Functions w/ Sets
```
# Basic Built-in Functions w/ Sets

example_set = set('hello') # set() turns an iterable into a set
print('example_set:', example_set)
print('--')

print('Number of Values:', len(example_set)) # length function
print('Minimum Value:', min(example_set)) # min function
print('Maximum Value:', max(example_set)) # max function
print('--')

# tuple to set
tup = (2,3,5,7)
print('tup to set:', set(tup))

# list to set
array = ['orange']*2 +  ['watermelon', 'apple'] + ['kiwi'] * 10
print('Original Array:', array)
print('list to set:', set(array))
```
```
example_set: {'o', 'e', 'h', 'l'}
--
Number of Values: 4
Minimum Value: e
Maximum Value: o
--
tup to set: {2, 3, 5, 7}
Original Array: ['orange', 'orange', 'watermelon', 'apple', 'kiwi', 'kiwi', 'kiwi', 'kiwi', 'kiwi', 'kiwi', 'kiwi', 'kiwi', 'kiwi', 'kiwi']
list to set: {'watermelon', 'orange', 'apple', 'kiwi'}
```
#### Basic Membership Operators
- Membership is one of the key operations with set because:
  - A set has no duplicates
  - A set’s membership operation is one of the fastest operations compared to strings, lists, or tuples this will be covered more when we look at the concept of: complexity
  - By using membership operator, we can be certain a target exists or does not exist in our data
```
# Membership Example
example_set = set('hello')

print("Membership of: \'h\'", 'h' in example_set)
print("Non-Membership of: \'z\'", 'z' not in example_set)
```
```
Membership of: 'h' True
Non-Membership of: 'z' True
```

#### Accessing Values in a Set
- Due to its unordered nature of a set, there is no concept of indexing or slicing with a set
  - However it is iterable
```
# Iteration of a Set
example_set = {2,3,5,7,11,13}

for v in example_set:
    print('Values of example_set:', v)
```
```
Values of example_set: 2
Values of example_set: 3
Values of example_set: 5
Values of example_set: 7
Values of example_set: 11
Values of example_set: 13
```

#### Python 3 Sets are mutable: Adding and Removing Values
- Sets are mutable -> can add and remove values
- There are also methods much lists that can affect the original sets as well
```
# Adding and Removing Values
languages = set() # empty set initialization

programming_languages = ['C', 'C#', 'Java', 'Python', 'HTML', 'CSS', 'JavaScript', 'Haskell']

for item in programming_languages:
    languages.add(item) # .add() method adds an item to a set

print('Languages set:', languages)
print('--')

languages.discard('HTML') # looks for the target value, if found, it will remove from the set
print('HTML deleted:', languages)

languages.remove('CSS') # remove can be used to delete a value;
# only difference is it will raise an error if the target is not found
print('CSS deleted:', languages)

random_remove = languages.pop() # .pop() method deletes a random value and return the value ... not recommended
print('Randomly Removed value:', random_remove)

languages.clear() # .clear() will empty out a set : output is set()
print('Empty languages:', languages)
```
```
Languages set: {'HTML', 'CSS', 'JavaScript', 'Python', 'Haskell', 'Java', 'C', 'C#'}
--
HTML deleted: {'CSS', 'JavaScript', 'Python', 'Haskell', 'Java', 'C', 'C#'}
CSS deleted: {'JavaScript', 'Python', 'Haskell', 'Java', 'C', 'C#'}
Randomly Removed value: JavaScript
Empty languages: set()
```

### Powering Up Sets: Set Operators
- Much like its mathematical counterpart, sets in Python 3 can utilize its vast operators to help us do complex calculations
  - Most of these operators will have a method counterpart because sets are mutable
- Note: We will be showcasing these operators with set of strings to make it easier, but this can be easily done with any kinds of sets
#### Our Operators
- Union 
- Intersection
- Difference
- Symmetric Difference
- Proper Subset
- Subset
- Proper Superset
- Superset

**Union:** The joining/combining of two sets
```
# Union Example:
set1 = set('hello')
set2 = set('world')

result = set1 | set2 # | is the union operator ... all the members of both set are combined to a single set
# Recall that: there are no duplicates
print('set1 union set 2:', result)
```
```
set1 union set 2: {'h', 'w', 'e', 'r', 'l', 'd', 'o'}
```
**Intersection:** Members/Items that only exists in both sets
```
# Union Example:
set1 = set('hello')
set2 = set('world')

result = set1 & set2 # & is the intersection operator
print('Intersection of set1 and set2:', result)
```
```
Intersection of set1 and set2: {'o', 'l'}
```
**Difference:** Members/items that only exists in the first set and not the second set
```
# Difference Example:
set1 = set('hello')
set2 = set('world')

result1 = set1 - set2 # - is the difference operator ... this is set1 difference set2
result2 = set2 - set1 # set2 difference set1

print('set1 - set2:', result1)
print('set2 - set1:', result2)
```
```
set1 - set2: {'e', 'h'}
set2 - set1: {'w', 'd', 'r'}
```
**Symmetric Difference:** Members/items that exists one or the other set, but not both sets
```
# Symmetric Difference Example:
set1 = set('hello')
set2 = set('world')

result = set1 ^ set2 # ^ is the symmetric difference operator

print('Symmetric Difference of:', result)
```
```
Symmetric Difference of: {'e', 'h', 'w', 'd', 'r'}
```
**Proper Subset:** This is a boolean operator
- A is proper subset of B if all members of A is found in B, but A cannot be exactly the same as B
```
# Proper Subset Example:
set1 = {1,2,3}
set2 = {1,2,3,4}
set3 = {1,2,3}
set4 = set('hello')

print('Is set1 proper subset of set2?:', set1 < set2) # < is the proper subset operator
print('Is set1 proper subset of set3?:', set1 < set3)
print('Is set1 proper subset of set4?:', set1 < set4)
```
```
Is set1 proper subset of set2?: True
Is set1 proper subset of set3?: False
Is set1 proper subset of set4?: False
```
**Subset:** This is a boolean operator
- A is a Proper Subset of B if A < B is True, but A can equal to B unlike a proper subset
```
# Subset Example:
set1 = {1,2,3}
set2 = {1,2,3,4}
set3 = {1,2,3}
set4 = set('hello')

print('Is set1 a subset of set2?:', set1 <= set2) # <= is the subset operator
print('Is set1 a subset of set3?:', set1 <= set3) # Notice the difference in value here
print('Is set1 a subset of set4?:', set1 <= set4)
```
```
Is set1 a subset of set2?: True
Is set1 a subset of set3?: True
Is set1 a subset of set4?: False
```
**Proper Superset:** This is a boolean operator
- A is a proper superset of B if A has all the values of B and more, but they are not equal to each other
```
# Superset Example:
set1 = {1,2,3,4}
set2 = {1,2,3,4}
set3 = {1,2,3}
set4 = set('hello')

print('Is set1 proper superset of set2?:', set1 > set2) # > is the proper superset operator
print('Is set1 proper superset of set3?:', set1 > set3)
print('Is set1 proper superset of set4?:', set1 > set4)
```
```
Is set1 proper superset of set2?: False
Is set1 proper superset of set3?: True
Is set1 proper superset of set4?: False
```
**Superset:** This is a boolean operator
- A is a superset of B if A > B or A == B
```
# Superset Example:
set1 = {1,2,3,4}
set2 = {1,2,3,4}
set3 = {1,2,3}
set4 = set('hello')

print('Is set1 superset of set2?:', set1 >= set2) # >= is the proper superset operator
print('Is set1 superset of set3?:', set1 >= set3)
print('Is set1 superset of set4?:', set1 >= set4)
```
```
Is set1 superset of set2?: True
Is set1 superset of set3?: True
Is set1 superset of set4?: False
```
### Disjoint: A Set Behaviour Property
- Two set are consided disjointed when two sets share no common value
  - Let A and B both represent a set
  - If A & B is empty, then set A and B are considered disjointed
  - To check this in python there is a method called: isdisjoint()
- Recall: & is the intersection operator
```
# Disjoint Example
# .isdisjoint() is a set method to check for such property between two sets.

set1 = {1,2,3,4}
set2 = {5,6,7}
set3 = {1,2,3,4,5}

print('set1 intersect set2:', set1 & set2) # Output is an empty set
print('set1 intersect set3:', set1 & set3) # Output is an non-empty set
print('--')
print('set 1 disjoint set 2 check:', set1.isdisjoint(set2)) # Therefore .isdisjoint() evaluates to True
print('set 1 disjoint set 3 check:', set2.isdisjoint(set3))
```
```
set1 intersect set2: set()
set1 intersect set3: {1, 2, 3, 4}
--
set 1 disjoint set 2 check: True
set 1 disjoint set 3 check: False
```

### Set Operators as Methods
```
# Union
a = set('abracadabra')
b = set('alacazam')

a.union(b)
print('Union:', a)

# Intersection
a = set('abracadabra')
b = set('alacazam')

a.intersection(b)
print('Intersection:', a)

# Difference
a = set('abracadabra')
b = set('alacazam')

a.difference(b)
print('Difference:', a)

# Symmeteric Difference
a = set('abracadabra')
b = set('alacazam')

a.symmetric_difference(b)
print('Symmetric Difference:', a)

# Subset
a = set('abracadabra')
b = set('alacazam')

print('Subset:', a.issubset(b))

# Superset
a = set('abracadabra')
b = set('alacazam')

print('Superset:', a.issuperset(b))
print('--')

# There are no proper subset/superset methods

# copy
a = set('abracadabra')
b = a.copy()
c = a

a.add('z')
print('.copy() examples:')
print('set a:', a)
print('set b:', b)
print('set c:', c)
```
```
Union: {'b', 'a', 'r', 'd', 'c'}
Intersection: {'b', 'a', 'r', 'd', 'c'}
Difference: {'b', 'a', 'r', 'd', 'c'}
Symmetric Difference: {'b', 'a', 'r', 'd', 'c'}
Subset: False
Superset: False
--
.copy() examples:
set a: {'b', 'a', 'z', 'r', 'd', 'c'}
set b: {'b', 'a', 'd', 'r', 'c'}
set c: {'b', 'a', 'z', 'r', 'd', 'c'}
```
#### Assignment Operation & Updating Methods
- This is a way to affect an original set with another and assign the result back to the original set
```
# Union and Update --> Update the set, adding elements from all others.
a = set('abracadabra')
b = set('alacazam')

a |= b # same as: a.update(b)
print('Union Update:', a)

# Intersection and Update --> Update the set, keeping only elements found in it and all others.
a = set('abracadabra')
b = set('alacazam')

a &= b # same as: a.intersection_update(b)
print('Intersection Update:', a)

# Difference and Update --> Update the set, removing elements found in others.
a = set('abracadabra')
b = set('alacazam')

a -= b # same as: a.difference_update(b)
print('Difference Update:', a)

# Symmetric Difference and Update --> Update the set, keeping only elements found in either set, but not in both.
a = set('abracadabra')
b = set('alacazam')

a ^= b # same as: a.symmetric_difference_update(b)
print('Symmeteric Difference Update:', a)
```
```
Union Update: {'b', 'a', 'z', 'r', 'l', 'm', 'd', 'c'}
Intersection Update: {'c', 'a'}
Difference Update: {'b', 'r', 'd'}
Symmeteric Difference Update: {'b', 'z', 'r', 'l', 'm', 'd'}
```

### Set Comprehension
Much like list comprehension, sets support comprehension as well
```
# Set Comprehension Example
def isPalindrome(x):
    ''' isPalindrome() returns True if string X is a palindrome '''
    return x == x[::-1]

nums = list(range(1,10000))
palindromic_set = {num for num in nums if isPalindrome(str(num))}

print('Palindromic Numbers Set from 1 to 10000:')
print(palindromic_set)
```

### Ending Notes on Sets for Python
- Sets aren’t sliceable nor indexable
- Sets cannot have sets inside them
- Sets do not have order; nor order of insertion
- Sets cannot guarantee that their values will be in order
- Sets do not record a value’s position

# Lesson 5: Dictionary
## Dictionary in Python 3
- Dictionary (Associative Array, map, symbol table) is a data type that stores a collection of (key, value) pairs, such that each possible key appears at most once in the collection
- **Common Operations:**
  - Adding a pair
  - Removing a pair
  - Modify an existing pair
  - Lookup of a value associated with a particular key
- Aside: This concept is an introduction to concepts similar to: hash table and search trees

### Defining a Dictionary in Python 3
- Dictionaries also use {} like sets
  - However, their individual item format is very different
- Each item in a dictionary be a pair of key: value
```
# Dictionary Example
sammy = {
    'username': 'sammy',
    'online': True,
    'followers': 42
}

# There are 3 items: each with their unique addresses and value
# Accessing
print('Sammy dict:', sammy)
print('Username:', sammy['username'])
print('Online Status:', sammy['online'])
print('Follower Count:', sammy['followers'])
```
```
Sammy dict: {'username': 'sammy', 'online': True, 'followers': 42}
Username: sammy
Online Status: True
Follower Count: 42
```

### Dictionary Properties
- Each item in a dictionary is a key, value pair
#### Keys
- Keys are unique address for a dictionary value’s location           

**Key Properties:**
- Must be immutable (strings, numbers, tuples, frozenset)
- Unique; therefore, two same key values cannot exist in a single dictionary
  - NEWEST CREATED ITEM with a duplicate KEY superceeds the previous declaration

#### Values
- Values of a dictionary within a key can be any data type

#### Updating a Dictionary
- We can modify existing values by referencing the key
- We can add new values to a dictionary by creating a new key
- We can overwrite a value at an existing key by referencing and recreating the value for it
```
# Update Example

sammy = {
    'username': 'sammy',
    'online': True,
    'followers': 42
}

sammy['followers'] += 10 # We are adding 10 to the value located at key: 'followers'
sammy['verified'] = True # We added a new value at a new key: 'verified'
sammy['username'] = 'SammySammy'

print('Sammy Dict:', sammy)
```
```
Sammy Dict: {'username': 'SammySammy', 'online': True, 'followers': 52, 'verified': True}
```

#### Deletion with Dictionary
- We can delete a key hence deleting the value connected to the key
- We can empty out the entire dictionary
- We can delete the dictionary (uncommonly used)
```
# Deletion Example

sammy = {
    'username': 'sammy',
    'online': True,
    'followers': 42
}

del sammy['followers'] # del is a keyword used to help us to execute a removal
print('followers key deleted:', sammy)

sammy.clear() # {} is considered an empty dict
print('emptying out a dictionary', sammy)
print('--\n\n')

del sammy
print('Deleting sammy, should create an error when referenced again', sammy)
```
```
followers key deleted: {'username': 'sammy', 'online': True}
emptying out a dictionary {}
--





---------------------------------------------------------------------------

NameError                                 Traceback (most recent call last)

<ipython-input-11-d3cbe81f2de2> in <module>
     15
     16 del sammy
---> 17 print('Deleting sammy, should create an error when referenced again', sammy)


NameError: name 'sammy' is not defined
```

#### Membership
- We can use the **in** and **not in** operators to check if a key exists in a dictionary
```
# Membership Example

sammy = {
    'username': 'sammy',
    'online': True,
    'followers': 42
}

print('Checking for key username:', 'username' in sammy)
print('Checking if followers is not a key:', 'followers' not in sammy)
```
```
Checking for key username: True
Checking if followers is not a key: False
```

#### Built-in Functions’ Interactions w/ Dictionaries
```
# Built-in Function Interactions

sammy = {
    'username': 'sammy',
    'online': True,
    'followers': 42
}

print('Size of sammy dict:', len(sammy))
print('Largest Key:', max(sammy))
print('Smallest Key:', min(sammy))
print('Dict to string:', str(sammy))
print('Dict to list:', list(sammy))
```
```
Size of sammy dict: 3
Largest Key: username
Smallest Key: followers
Dict to string: {'username': 'sammy', 'online': True, 'followers': 42}
Dict to list: ['username', 'online', 'followers']
```

#### Duplicate a Dictionary and Copy Keys Only
```
# Duplicate a Dictionary

sammy = {
    'username': 'sammy',
    'online': True,
    'followers': 42
}

sammy_copy1 = sammy.copy()
sammy_copy2 = sammy

sammy['verified'] = True

print('sammy_copy1:', sammy_copy1)
print('sammy_copy2:', sammy_copy2)
print('--')

# Duplicate keys only

tammy = tammy.fromkeys(sammy) # Notice that all key's values are None ... aka empty

print('tammy dict:', tammy)
```
```
sammy_copy1: {'username': 'sammy', 'online': True, 'followers': 42}
sammy_copy2: {'username': 'sammy', 'online': True, 'followers': 42, 'verified': True}
--
tammy dict: {'username': None, 'online': None, 'followers': None, 'verified': None}
```

### Dictionary Methods
- To help power this awesome data structure, it has good set of methods for us to use
- Let A and B be a dictionary
  - A.keys() –> Returns a sequence of keys/addresses in A
  - A.values() –> Returns a sequence of item values in A
  - A.items() –> Returns a sequence of key,item pairs in A
  - A.get(address) –> Returns the item value at address
  - A.update(B) –> Extends A with the dictionary of key,value pairs of B
```
# Dictionary Method Examples

sammy = {
    'username': 'sammy',
    'online': True,
    'followers': 42
}

sammy_hidden = {
    'pwd' : 'qwerty',
    'location' : 'Toronto, Ontario'
}

# printing all the keys of a dict
print('Sammy Dict Keys:', sammy.keys()) # notice how it prints

sammy_keys = list(sammy.keys()) # we can listify the .keys() returned
print('List of sammy_keys', sammy_keys)
print('--')

# printing all the values of a dict
print('Sammy Dict Values:', sammy.values())
print('Sammy Dict Values as a list:', list(sammy.values()))
print('--')

# printing key, value pair of a dict
print('Sammy Dict key, value pairs:', sammy.items())
print('Sammy Dict key, value pairs as a list:', list(sammy.items()))
print('--')

# getting a value from a dict
print('Sammy followers value:', sammy.get('followers'))
print('Same as:', sammy['followers'])
print('--')

# updating / extending a dictionary
sammy.update(sammy_hidden)

print('Sammy extended with its hidden values:', sammy)
```
```
Sammy Dict Keys: dict_keys(['username', 'online', 'followers'])
List of sammy_keys ['username', 'online', 'followers']
--
Sammy Dict Values: dict_values(['sammy', True, 42])
Sammy Dict Values as a list: ['sammy', True, 42]
--
Sammy Dict key, value pairs: dict_items([('username', 'sammy'), ('online', True), ('followers', 42)])
Sammy Dict key, value pairs as a list: [('username', 'sammy'), ('online', True), ('followers', 42)]
--
Sammy followers value: 42
Same as: 42
--
Sammy extended with its hidden values: {'username': 'sammy', 'online': True, 'followers': 42, 'pwd': 'qwerty', 'location': 'Toronto, Ontario'}
```

### Iterating a Dictionary
- We will be taking advantage of three iteration methods
  - iterating the keys
  - iterating the values
  - iterating the key, value pairs by unpacking
```
# Iteration Example 1: Keys
sammy = {
    'username': 'sammy',
    'online': True,
    'followers': 42
}

for k in sammy.keys():
    print('Current key:', k)
print('--\n')

# Iteration Example 2: Values

for v in sammy.values():
    print('Current value:', v)
print('--\n')

# Iteration Example 3: Key, Value Pair

for k, v in sammy.items():
    print('Current Key:', k)
    print('Current Value:', v)
    print()
```
```
Current key: username
Current key: online
Current key: followers
--

Current value: sammy
Current value: True
Current value: 42
--

Current Key: username
Current Value: sammy

Current Key: online
Current Value: True

Current Key: followers
Current Value: 42
```

### dict() Constrcutor Dictionary Comprehension
- We can turn other data types to dictionaries
- Also similar to lists, tuples, and sets, dictionaries also support comprehension
- **Note:** We must specify where the keys are and where the values
```
# dict() Example

example_data = [
    ('one', 3),
    ('two', 3),
    ('three', 5)
]

data_dict = dict(example_data)
print('data_dict:', data_dict)
print('--')

# Dictionary Comprehension
# Goal: Take string numerals and assign them with their integer square
# - keys : string numerals
# - values: integer squares

example_data2 = ['1', '2', '3', '4', '5']

data2_dict = {x : int(x)**2 for x in example_data2}

print('data2_dict:', data2_dict)
```
```
data_dict: {'one': 3, 'two': 3, 'three': 5}
--
data2_dict: {'1': 1, '2': 4, '3': 9, '4': 16, '5': 25}
```
