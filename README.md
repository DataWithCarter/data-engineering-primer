# data-engineering-primer
* [Python](#python)
* [Scala](#scala)
* [MySQL](#mysql)
* [Apache Spark](#apache-spark)
* [Apache Airflow](#apache-airflow)
* [Apache Flink](#apache-flink)
* [Apache Kafka](#apache-kafka)

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

### Strings (immutable):
```py
s = "Hello"
s += ', World!' # "Hello, World!"

# For more complex formatting...
s = 'Hi {} how is your {} going?'.format('Tiffany', 'project') # Hi Tiffany how is your project going?

# String --> Integer
int("1000") # 1000

# Integer --> String
str(1000) # "1000"

# Array --> String
arrayOfStrings = ['a', 'b', 'c']
newString = ''.join(arrayOfStrings) # 'abc'

# Grab ASCII value of character
ord("a") # 97
```

### Arrays:
```py
# Initialize
arr = [0, 1, 2, 3, 4]
arr = [0] * 5 # [0, 0, 0, 0, 0]

# Initialize with List comprehension
arr = [i for i in range(5)] # [0, 1, 2, 3, 4]
arr = [[0] * 3 for i in range(4)] #  [[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]] <--- 2-D array

# Get length
arr = [0, 1, 2, 3, 4]
length = len(arr) # length = 5

# Add/ Remove
arr = [0, 1, 2, 3, 4]
arr.pop() # [0, 1, 2, 3] <-- remove from the end
arr.append(4) # [0, 1, 2, 3, 4] <-- add to the end
arr.insert(1, 1) # [0, 1, 1, 2, 3, 4] <-- at the index 1, add 1
arr.remove(1) # [0, 1, 2, 3, 4] <-- removes the first instance of the value '1' in the array
del a[3] # [0, 1, 2, 4] <-- removes the value at the specified index
del a[1:-1] # [0, 4] <-- removes values from 2nd index up to the second last index

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

# Custom Sorting
arr = ['a', 'ccc', 'bb']
arr.sort(key=lambda x: len(x)) # ['a', 'bb', 'ccc']
arr.sort(key=lambda x: - len(x)) # ['ccc', 'bb', 'a'] <-- add a '-' to do it in reverse
```

#### Functions:
```py
def addOne(num):
  newNum = num + 1
  return newNum

addOne(1) # returns 2
```

### Conditional Statements:
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

# Check if value is in a list
if name in ['john', 'cathy', 'diego']:
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
for i in range(5):
  print(i) # 0, 1, 2, 3, 4

for i in range(2, 5):
  print(i) # 2, 3, 4

# backwards for-loop
nums = [10, 20, 30]
for i in range(len(nums) -1, -1, -1):
  print(nums[i]) # 30, 20, 10

# for-each loop
for num in [10, 20, 30]:
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

## Scala

## MySQL

## Apache Spark

## Apache Airflow

## Apache Kafka

## Apache Flink