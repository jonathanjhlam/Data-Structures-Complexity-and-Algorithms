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
