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
