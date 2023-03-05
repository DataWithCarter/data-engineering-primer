# The Data Engineering Primer
- [The Data Engineering Primer](#the-data-engineering-primer)
  - [CLI \& Vim](#cli--vim)
  - [Git](#git)
  - [Python](#python)
      - [Variables:](#variables)
      - [Functions:](#functions)
      - [Conditional Statements:](#conditional-statements)
      - [Loops:](#loops)
      - [Strings (Immutable):](#strings-immutable)
      - [Arrays:](#arrays)
      - [HashMap](#hashmap)
      - [HashSet](#hashset)
      - [Double Ended Queue (FIFO):](#double-ended-queue-fifo)
      - [Stacks (LIFO):](#stacks-lifo)
      - [Heaps:](#heaps)
      - [Tuples (Immutable)](#tuples-immutable)
      - [Classes:](#classes)
  - [MySQL](#mysql)
  - [Apache Spark (PySpark)](#apache-spark-pyspark)
  - [Apache Airflow](#apache-airflow)
  - [Amazon Web Services (AWS)](#amazon-web-services-aws)
  - [Great Expecations](#great-expecations)
  - [Data Build Tool (DBT)](#data-build-tool-dbt)
  - [Scala](#scala)
      - [The Fundamentals: variables, comments, printing, and math :D](#the-fundamentals-variables-comments-printing-and-math-d)
      - [Conditional Statements](#conditional-statements-1)
      - [Loops](#loops-1)
      - [Lists](#lists)
      - [Functions](#functions-1)
  - [Apache Kafka](#apache-kafka)
  - [Apache Flink](#apache-flink)
  - [Databricks](#databricks)
  - [Kubernetes](#kubernetes)

## CLI & Vim
## Git
## Python
#### Variables:
```py
# method 1: single assignment
x = 1
y = 2

# method 2: multiple assignment
x, y = 1, False

# method 3: multiple assignment (all with same value)
x = y = 1
```

#### Functions:
```py
def addOne(num):
  newNum = num + 1
  return newNum

addOne(1) # returns 2
```

#### Conditional Statements:
```py
# Standard If Statement
if num = 1:
  # ...
elif num == 2:
  # ...    
else:
  # ...

# Check within a given range
if 1 <= num <= 2:
  # ...

# One-liners
result = 1000 if score >= 100 else 5

# Switch-Case
match score:
  case 1000:
    print("Yay you got a score of precisely 1000!")
  case 500:
    print("Woah you got a score of exactly 500!")
  case _: # Default Case
    print("Your score was neither 1000 nor 500. Try again!")
```

#### Loops:
```py
# while-loop
i = 0
while i < 10:
  i += 1

# standard for-loops
for i in range(5): # note end amount is non-inclusive
  print(i) # 0, 1, 2, 3, 4

for i in range(2, 5): # note start amount is inclusive
  print(i) # 2, 3, 4

# iterate backwards
for i in range(3, -1, -1): # define start, end (non-inclusive), decrement amount
  print(i) # 3, 2, 1, 0
```

#### Strings (Immutable):
```py
s = "Hello"
s += ', World!'
>>> "Hello, World!"

# For more complex formatting...
s = 'Hi {} how is your {} going?'.format('Tiffany', 'project')
>>> Hi Tiffany how is your project going?

# String --> Integer
int("1000")
>>> 1000

# Integer --> String
str(1000)
>>> "1000"

# Array --> String
arrayOfStrings = ['a', 'b', 'c']
newString = ''.join(arrayOfStrings)
>>> 'abc'

# 2-D Array --> 1-D Array of strings
2dArray = [['a', 'b', 'c'], ['a', 'b', 'c']]
arrayOfStrings = ["".join(row) for row in 2dArray]
>>> ['abc', 'abc']

# Grab ASCII value of character
ord("a")
>>> 97

# Convert Binary String to integer equivalent
int("1000", 2)
>>> 8

# Integer to Binary
format(3,'b')
>>> '11'
```

#### Arrays:
```py
# Initialize
arr = [0, 1, 2, 3, 4]
>>> [0, 1, 2, 3, 4]

arr = [0] * 5
>>> [0, 0, 0, 0, 0]

# Get length
arr = [0, 1, 2, 3, 4]
length = len(arr)
>>> 5

# Initialize 1-D Array with List comprehension
arr = [i for i in range(5)]
>>> [0, 1, 2, 3, 4]

# Initialize 2-D Array with List comprehension 
arr = [[0] * 3 for i in range(4)] 
>>> [[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]]

# Get column and row length
rows = len(arr)
>>> 4

cols = len(arr[0])
>>> 3

# Add/ Remove
arr = [0, 1, 2, 3, 4]
arr.pop() # [0, 1, 2, 3] <-- remove from the end
arr.append(4) # [0, 1, 2, 3, 4] <-- add to the end
arr.insert(1, 1) # [0, 1, 1, 2, 3, 4] <-- at the index 1, add 1
arr.remove(1) # [0, 1, 2, 3, 4] <-- removes the first instance of the value '1' in the array
del a[3] # [0, 1, 2, 4] <-- removes the value at the specified index
del a[1:-1] # [0, 4] <-- removes values from 2nd index up to the second last index
arr += [5, 6, 7] # [0, 4, 5, 6, 7] <-- concatenate arrays

# Update Cells
arr = [1, 3, 2, 4]
arr[0] = 100 # [100, 1, 2, 3, 4]
arr[2] = 999 # [100, 1, 999, 3, 4]
arr[-1] = 3000 # [100, 1, 9999, 3, 3000] <-- -1 represents last index
arr[-2] = 12345 # [100, 1, 9999, 12345, 3000] <-- -2 represents second last index

# Sorting
arr = [1, 3, 2, 4]
arr.reverse() # [4, 2, 3, 1] <-- simply reverses the array
arr.sort() # [1, 2, 3, 4] <-- sorts in increasing order
arr.sort(reverse=True) # [4, 3, 2, 1] <-- sorts in decreasing order

newArray = arr[::-1] # [4, 2, 3, 1] <-- (reverse but not in place)
for i in range(len(mat)): # reverse each row in matrix
  mat[i] = mat[i][::-1]

# Custom Sorting
arr = ['a', 'ccc', 'bb']
arr.sort(key=lambda x: len(x)) # ['a', 'bb', 'ccc']
arr.sort(key=lambda x: - len(x)) # ['ccc', 'bb', 'a'] <-- add a '-' to do it in reverse
 
arr = [[1, 2], [5, 4], [1, 4]]
arr.sort(key=lambda x: (-x[0], x[1])) # [[5, 4], [1, 2], [1, 4]]

# Check if value is in a list
if name in ['john', 'cathy', 'diego']:
  # ...

# Compare lists
arr1, arr2 = [1, 2, 3], [2, 3, 4]
if arr1 == [1, 2, 3]:
  return True
elif arr1 == arr2:
  return False

# array with for-loop
nums = [10, 20, 30]
for i in range(len(nums)):
  print(nums[i]) # 10, 20, 30

# array backwards with for-loop
nums = [10, 20, 30]
for i in range(len(nums) -1, -1, -1):
  print(nums[i]) # 30, 20, 10

# for-each loop
for num in [10, 20, 30]: # you can swap this with a reference to an array
  print(num) # 10, 20, 30

# for-each loop with current index
for i, num in enumerate([10, 20, 30]):
  print(i, num) # 0 10, 1 20, 2 30

# zip - look at 2+ arrays at a time
for num1, num2 in zip([0, 1, 2], [0, 100, 200, 300]):
  print(num1, num2) # 0 0, 1 100, 2 200 <-- note: it won't print 300 as its bounded by shortest array length.
  
# look at columns in 2-d array or array of strings:
stringArr = ["abc", "123", "xyz"]
for l1, l2, l3 in zip(*stringArr):
  print(l1, l2, l3) # a 1 x, b 2 y, c 3 z
```

#### HashMap
```py
nameToAge = {'Diego': 32, 'Evelyn': 22, 'Thomas': 29}
nameToAge['Jayden'] = 45
nameToAge.pop('Thomas')
>>> {'Diego': 32, 'Evelyn': 22, 'Jayden': 45}

# Get length
len(nameToAge)
>>> 3

# Check if key is in hashmap
if 'Murray' not in nameToAge:
  nameToAge['Murray'] = 60
>>> {'Diego': 32, 'Evelyn': 22, 'Jayden': 45, 'Murray': 60}

# Build HashMap with dict comprehension
hm = { i:i*10 for i in range(10) if i % 2 == 0}
>>> {0: 0, 2: 20, 4: 40, 6: 60, 8: 80}

# Hashmaps with loops:
for name in nameToAge:
  # 'Diego', 'Evelyn', 'Jayden', 'Murray'

for age in nameToAge.values():
    # 32, 22, 45, 60

for name, age in myMap.items():
  # 'Diego' 32, 'Evelyn' 22, 'Jayden' 45, 'Murray' 60
  
# Clear an entire HashMap:
nameToAge.clear()
>>> {}

# Default dict: Used to prevent errors when incrementing/ adding to hashmap as there will be default value
graph = collections.defaultdict(list) # default value is []
graph[0].append(1)
graph[0].append(2)
>>> {0: [1, 2]}

ages = collections.defaultdict(int) # default value is 0
ages['alice']+= 1
>>> {'alice': 1}

# Counter: Used to easily count the number of occurences
counter = collections.Counter([1, 1, 2, 1, 2, 1, 3])
>>> {1:4, 2:2, 3:1}

counter.most_common() # returns list of sorted keys ordered by occurences in descending order
>>> [(1, 4), (2, 2), (3, 1)]
```

#### HashSet
```py
# O(1) - Add/ remove from set
hs = set()
hs.add(1)
hs.add(2)
hs.remove(1)
>>> {2, 3}

# O(1) - Get length
print(len(mySet))
>>> 2

# O(1) - Check if a value is in the set
if 5 in hs:
  // do something ...

# O(n) - list to set
hs = set([1, 2, 3, 4, 5])
>>> {1, 2, 3, 4, 5}

# O(n) - Set comprehension with conditional statement
hs = { i for i in range(6) if i % 2 == 1}
>>> {1, 3, 5}
```

#### Double Ended Queue (FIFO):
```py
# O(1) - insert
queue = collections.deque()
queue.append(1)
queue.append(2)
queue.append(3)
>>> deque([1, 2, 3])

# O(1) - removal
queue.popleft()
>>> deque([2, 3])

# You can also append to the left, and pop from the right...
queue = deque()
queue.appendleft(1)
queue.appendleft(2)
>>> deque([2, 1])

queue.pop()
>>> deque([1])

# O(n) - list to queue
queue = deque([1, 2, 3])
>>> deque([1, 2, 3])
```

#### Stacks (LIFO):
```py
# Using Array
stack = []
  
# O(1) - push to stack
stack.append('a')
stack.append('b')
stack.append('c')
print(stack)
>>> ['a', 'b', 'c']
  
#  O(1) - pop from stack
print(stack.pop())
>>> ['c']

# Using deque with append() and pop()
queue = collections.deque()
queue.append(1)
queue.append(2)
queue.pop()
print(queue)
>>> deque([1])

# Using deque with appendleft() and popleft()
queue = collections.deque()
queue.appendleft(1)
queue.appendleft(2)
queue.popleft()
print(queue)
>>> deque([1])
```

#### Heaps:
```py
# nlog(n) - array --> heap
minHeap = [2, 1, 3, 5, 4]
heapq.heapify(minHeap)
>>> [1, 2, 3, 4, 5]

# log(n) - for each individual push to heap (nlog(n) for them all)
minHeap = []
heapq.heappush(minHeap, 3)
heapq.heappush(minHeap, 1)
heapq.heappush(minHeap, 2)
>>> [1, 2, 3]

# log(n) - for each individual pop from heap (nlog(n) for them all)
while len(minHeap):
    heapq.heappop(minHeap)
>>> 1, 2, 3

# O(1) - index lookup
minVal = minHeap[0] # min @ index 0
maxVal = minHeap[-1] # max @ last index

# For max heaps the workaround is to negate your values
# Remember to negate your values once again after popping!
maxHeap = []
heapq.heappush(maxHeap, -3)
heapq.heappush(maxHeap, -1)
heapq.heappush(maxHeap, -2)
>>> -3, -2, -1

minVal = maxHeap[0] # min @ last index
maxVal = maxHeap[-1] # max @ index 0
```

#### Tuples (Immutable)
```py
tup1 = (1, 2, 3, 4)
print(tup[1])
>>> 2
print(tup[-1])
>>> 4

# Unlike arrays they can be a Key in a hashmap or hashset!!
hm = { (1,1): 1, (1,2): 2, (1,3): 3}
print(myMap[(1,2)])
>>> 2

hs = set()
hs.add((1,1))
hs.add((1,2))
hs.add((1,3))
print(hs)
>>> {(1, 1), (1, 2), (1, 3)}
```

#### Classes:
```py
class Dog:
  # note: this is a python 'magic method' used to indicate the constructor
  def __init__(self, name):
    self.name = name
    self.age = 0
    
  # note: optional arguments with default value
  def incrementAge(self, increment = 1):
    self.age += increment

  # note: 'self' is required
  def speak(self):
    print('{} says: Scooby Doobie Doooo I\'m {} years old!'.format(self.name, self.age))

scooby = Dog('Scooby-Doo')

scooby.incrementAge()
scooby.speak() 
>>> Scooby-Doo says: Scooby Doobie Doooo I'm 1 years old!

scooby.incrementAge(7)
scooby.speak()
>>> Scooby-Doo says: Scooby Doobie Doooo I'm 8 years old!
```

## MySQL

## Apache Spark (PySpark)

## Apache Airflow

## Amazon Web Services (AWS)

## Great Expecations

## Data Build Tool (DBT)

## Scala
#### The Fundamentals: variables, comments, printing, and math :D
Scala can automatically figure out what data type your variable is based on what type of data you're storing in the variable. 

```scala
// Variables defined by 'var' can be changed!
var var1 = "I can be changed!"!  # mutable

// Values defined by 'val' can never be changed!
val val1 = "I cannot be changed!"a # immutable

// If you haven't noticed yet use '//' to make single line comments!!

/*
  To do
  multi-line
  comments

  ...
  do this (note the '/*' around this comment)
*/

// Print something to the screen (great for debugging too!)
println("Hello, Everyone!")
>>> "Hello, Everyone"
```
#### Conditional Statements
```scala
// Standard if-else statement
if ((score >= 500) || (score <= 100)) { // the curly braces aren't necessary!!
  println("You won the grand prize!")
}
else if ((score >= 200) && (score <= 400)) {
  println("You won a prize!!")
}
else {
  println("Try again!")
}

// One line if-else (like java ternary operator)
val score = 300
var result = if (score >= 250) "You won!" else "Try again!"
>>> "You won!"
```

#### Loops
```scala
// while loop
i = 0
while (i<3) {
  println(i)
  i+=1
}
>>> 0
>>> 1
>>> 2

// do-while loop (enters loop at least once)
i = 0
do {
  println(i)
  i+=1
} while (i == -1)
>>> 0

// For-loop
for (i <- 1 to 3) // note: 'to' is inclusive
  println(i)
>>> 1
>>> 2
>>> 3

for (i <- 1 until 10) // note: 'until' is non-inclusive
  println(i)
>>> 1
>>> 2
```
#### Lists
```scala
// create a list
var myList = List(1, 2, 3)

// for-each loop
for (num <- myList)
  println(num)
>>> 1
>>> 2
>>> 3

// create a list with for-each loop & conditional statements
var evenList = for { i <- 1 to 20 
  if (i % 2) == 0  
  } yield i
>>> [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]

// Nested for-loop (this is honestly super interesting)
for ( i <- 1 to 3; j <- 7 to 9) 
  println("i: " + i +", j: " + j)
>>> i: 1, j: 7 
>>> i: 1, j: 8 
>>> i: 1, j: 9 
>>> i: 2, j: 7 
>>> i: 1, j: 8 
>>> i: 2, j: 9 
>>> i: 3, j: 7 
>>> i: 1, j: 8 
>>> i: 3, j: 9 

// break does not exist in scala
// instead put loop in function and use 'return' instead of break
def exampleFunction() {
  for ( i <- 1 to 10) {
    if (i == 5) {
      return // workaround to break out of loop
    }
  }
}
exampleFunction() // call function

// coninue does not exist in scala as well...
// instead just don't invert the boolean logic and perform other logic in if statement
for ( i <- 1 to 10) {
  if (i == 5) { // workaround for 'if i != 5 then continue'
    // do something ...
  }
}

```

#### Functions
```scala
def doSomething() {
  println("I'm doing something!!")
}

doSomething()
```

## Apache Kafka

## Apache Flink

## Databricks

## Kubernetes
