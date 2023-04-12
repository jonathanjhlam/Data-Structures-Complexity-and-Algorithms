# Data Structures Complexity and Algorithms
Notes for Unit: 03 - Algorithms & Data Structures      

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
