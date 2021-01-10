# Python Topgear Assignment L1

Using Python 3.8.6, I am solving this Python Assignment Questions

## Question 1
Given a list, url = [www.annauniv.edu, www.google.com, www.ndtv.com, www.website.org, www.bis.org.in, www.rbi.org.in]; Sort the list based on the top level domain (edu, com, org, in) using custom sorting

Code

```python
url = ['www.annauniv.edu', 'www.google.com', 'www.ndtv.com', 'www.website.org', 'www.bis.org.in', 'www.rbi.org.in']
def tld(item):
  return item[item.rfind('.')+1:]

print("The sorted list would be ", sorted(url, key=tld))
```

Output

```bash
The sorted list would be  ['www.google.com', 'www.ndtv.com', 'www.annauniv.edu', 'www.bis.org.in', 'www.rbi.org.in', 'www.website.org']
```

## Question 2
Given a list of strings, return the count of the number of strings where the string length is 2 or more and the first and last chars of the string are the same.  

i.	['axa', 'xyz', 'gg', 'x', 'yyy']
ii.	['x', 'cd', 'cnc', 'kk']
iii.	['bab', 'ce', 'cba', 'syanora']

Code

```python
l1 = ['axa', 'xyz', 'gg', 'x', 'yyy']
l2 = ['x', 'cd', 'cnc', 'kk']
l3 = ['bab', 'ce', 'cba', 'syanora']

def lenofstring(list):
  count = 0
  for item in list:
    if item[0] == item[-1] and len(item) >= 2:
      count += 1
  return count

print(f"The Length for L1 would be { lenofstring(l1) },\nThe Length for L1 would be { lenofstring(l2) },\nThe Length for L1 would be { lenofstring(l3) }")
```

Output

```bash
The Length for L1 would be 3,
The Length for L1 would be 2,
The Length for L1 would be 1
```

## Question 3
Given a list of strings, return a list with the strings in sorted order, except group all the strings that begin with 'x' first.  e.g. ['mix', 'xyz', 'apple', 'xanadu', 'aardvark'] yields ['xanadu', 'xyz', 'aardvark', 'apple', 'mix']. 
Hint: this can be done by making 2 lists and sorting each of them before combining them.

i.	['bbb', 'ccc', 'axx', 'xzz', 'xaa']
ii.	['mix', 'xyz', 'apple', 'xanadu', 'aardvark']

Code

```python
a = ['bbb', 'ccc', 'axx', 'xzz', 'xaa']
b = ['mix', 'xyz', 'apple', 'xanadu', 'aardvark']

def sorting(list):
  tmp1 = [e for e in list if e.startswith('x')]
  tmp2 = [e for e in list if not e.startswith('x')]
  tmp1.sort()
  tmp2.sort()
  return tmp1 + tmp2

print(f"Sorted output for List A: { sorting(a) }\nSorted output for List B: { sorting(b) }")
```

Output

```bash
Sorted output for List A: ['xaa', 'xzz', 'axx', 'bbb', 'ccc']
Sorted output for List B: ['xanadu', 'xyz', 'aardvark', 'apple', 'mix']
```

## Question 4
Given a list of non-empty tuples, return a list sorted in increasing order by the last element in each tuple. 
e.g. [(1, 7), (1, 3), (3, 4, 5), (2, 2)] yields [(2, 2), (1, 3), (3, 4, 5), (1, 7)]
Hint: use a custom key= function to extract the last element form each tuple.

i.	 [(1, 3), (3, 2), (2, 1)]
ii.	[(1, 7), (1, 3), (3, 4, 5), (2, 2)]

Code

```python
l1 = [(1, 3), (3, 2), (2, 1)]
l2 = [(1, 7), (1, 3), (3, 4, 5), (2, 2)]

def getLastEle(tup):
  return tup[-1]

print(f"Sorted output for L1: { sorted(l1, key=getLastEle) }\nSorted output for L2: { sorted(l2, key=getLastEle) }" )
```

Output

```bash
Sorted output for L1: [(2, 1), (3, 2), (1, 3)]
Sorted output for L2: [(2, 2), (1, 3), (3, 4, 5), (1, 7)]
```

## Question 5
Given a list of numbers, return a list where all adjacent == elements have been reduced to a single element, so [1, 2, 2, 3] returns [1, 2, 3]. You may create a new list or modify the passed in list.

i.	 [1, 2, 2, 3], [2, 2, 3, 3, 3]

Code

```python
list1 = [1, 2, 2, 3]
list2 = [2, 2, 3, 3, 3]

def changelist(l1):
  temp = []
  temp.append(l1[0])
  for i, e in enumerate(l1):
    if i+1 < len(l1):
      if l1[i+1] != e:
        temp.append(l1[i+1])
  return temp

print(f"The Refined List for L1: { changelist(list1) }\nThe Refined List for L2: { changelist(list2) }")
```

Output

```bash
The Refined List for L1: [1, 2, 3]
The Refined List for L2: [2, 3]
```

## Question 6
Write a function to print the information in the dictionary(bookstore) in the given format

bookstore={"New Arrivals":{"COOKING":["Everyday Italian","Giada De Laurentiis","2005","30.00"],"CHILDREN":["Harry Potter”, J K. Rowling","2005","29.99"],"WEB":["Learning XML","Erik T. Ray","2003","39.95"]}}

BOOKSTORE
['Learning XML', 'Erik T. Ray', '2003', '39.95']
['Everyday Italian', 'Giada De Laurent is', '2005', '30.00']
['Harry Potter', 'J K. Rowling', '2005', '29.99']

Code

```python
bookstore={"New Arrivals":{"COOKING":["Everyday Italian","Giada De Laurentiis","2005","30.00"],"CHILDREN":["Harry Potter”, J K. Rowling","2005","29.99"],"WEB":["Learning XML","Erik T. Ray","2003","39.95"]}}

for items in bookstore.values():
  for item in sorted(items.items(), key=lambda a: a[0], reverse=True):
    print(item[1])
```

Output

```bash
['Learning XML', 'Erik T. Ray', '2003', '39.95']
['Everyday Italian', 'Giada De Laurentiis', '2005', '30.00']
['Harry Potter”, J K. Rowling', '2005', '29.99']
```

# Question 7
Given a string, str1=""”Python is a widely used high-level programming language for general-purpose programming, created by Guido van Rossum and first released in 1991. An interpreted language, Python has a design philosophy which emphasizes code readability (notably using whitespace indentation to delimit code blocks rather than curly braces or keywords), and a syntax which allows programmers to express concepts in fewer lines of code than possible in languages such as C++ or Java. The language provides constructs intended to enable writing clear programs on both a small and large scale .Python features a dynamic type system and automatic memory management and supports multiple programming paradigms, including object-oriented, imperative, functional programming, and procedural styles. It has a large and comprehensive standard library. Python interpreters are available for many operating systems, allowing Python code to run on a wide variety of systems. CPython, the reference implementation of Python, is open source software and has a community-based development model, as do nearly all of its variant implementations. CPython is managed by the non-profit Python Software Foundation."""

a.	Build a dictionary, with "words as key" --> Frequency of occurrence as value
E.g. Python --> 7, is --> 3
b.	Print the top 5 words with their frequency of occurrence

Code

```python
str1="""Python is a widely used high-level programming language for general-purpose programming, created by Guido van Rossum and first released in 1991. An interpreted language, Python has a design philosophy which emphasizes code readability (notably using whitespace indentation to delimit code blocks rather than curly braces or keywords), and a syntax which allows programmers to express concepts in fewer lines of code than possible in languages such as C++ or Java. The language provides constructs intended to enable writing clear programs on both a small and large scale .Python features a dynamic type system and automatic memory management and supports multiple programming paradigms, including object-oriented, imperative, functional programming, and procedural styles. It has a large and comprehensive standard library. Python interpreters are available for many operating systems, allowing Python code to run on a wide variety of systems. CPython, the reference implementation of Python, is open source software and has a community-based development model, as do nearly all of its variant implementations. CPython is managed by the non-profit Python Software Foundation."""

wordCountTable = {}
wordList = str1.split()
for word in wordList:
  wordCountTable[word]=str1.count(word)

print(f"The Dictionary is { wordCountTable }")
print(f"Top 5 elements in the Dictionary is { sorted(wordCountTable.items(), key=lambda a: a[1], reverse=True)[0:5] }")
```

Output

```bash
The Dictionary is {'Python': 9, 'is': 3, 'a': 93, 'widely': 1, 'used': 1, 'high-level': 1, 'programming': 4, 'language': 4, 'for': 2, 'general-purpose': 1, 'programming,': 2, 'created': 1, 'by': 2, 'Guido': 1, 'van': 1, 'Rossum': 1, 'and': 9, 'first': 1, 'released': 1, 'in': 18, '1991.': 1, 'An': 1, 'interpreted': 1, 'language,': 1, 'has': 4, 'design': 1, 'philosophy': 1, 'which': 2, 'emphasizes': 1, 'code': 4, 'readability': 1, '(notably': 1, 'using': 1, 'whitespace': 1, 'indentation': 1, 'to': 5, 'delimit': 1, 'blocks': 1, 'rather': 1, 'than': 2, 'curly': 1, 'braces': 1, 'or': 8, 'keywords),': 1, 'syntax': 1, 'allows': 1, 'programmers': 1, 'express': 1, 'concepts': 1, 'fewer': 1, 'lines': 1, 'of': 7, 'possible': 1, 'languages': 1, 'such': 1, 'as': 8, 'C++': 1, 'Java.': 1, 'The': 1, 'provides': 1, 'constructs': 1, 'intended': 1, 'enable': 1, 'writing': 1, 'clear': 1, 'programs': 1, 'on': 19, 'both': 1, 'small': 1, 'large': 2, 'scale': 1, '.Python': 1, 'features': 1, 'dynamic': 1, 'type': 1, 'system': 3, 'automatic': 1, 'memory': 1, 'management': 1, 'supports': 1, 'multiple': 1, 'paradigms,': 1, 'including': 1, 'object-oriented,': 1, 'imperative,': 1, 'functional': 1, 'procedural': 1, 'styles.': 1, 'It': 1, 'comprehensive': 1, 'standard': 1, 'library.': 1, 'interpreters': 1, 'are': 3, 'available': 1, 'many': 1, 'operating': 1, 'systems,': 1, 'allowing': 1, 'run': 1, 'wide': 2, 'variety': 1, 'systems.': 1, 'CPython,': 1, 'the': 3, 'reference': 1, 'implementation': 2, 'Python,': 2, 'open': 1, 'source': 1, 'software': 1, 'community-based': 1, 'development': 1, 'model,': 1, 'do': 2, 'nearly': 1, 'all': 4, 'its': 1, 'variant': 1, 'implementations.': 1, 'CPython': 2, 'managed': 1, 'non-profit': 1, 'Software': 1, 'Foundation.': 1}

Top 5 elements in the Dictionary is [('a', 93), ('on', 19), ('in', 18), ('Python', 9), ('and', 9)]
```

## Question 8
Given a string, str1=""”Python is a widely used high-level programming language for general-purpose programming, created by Guido van Rossum and first released in 1991. An interpreted language, Python has a design philosophy which emphasizes code readability (notably using whitespace indentation to delimit code blocks rather than curly braces or keywords), and a syntax which allows programmers to express concepts in fewer lines of code than possible in languages such as C++ or Java. The language provides constructs intended to enable writing clear programs on both a small and large scale .Python features a dynamic type system and automatic memory management and supports multiple programming paradigms, including object-oriented, imperative, functional programming, and procedural styles. It has a large and comprehensive standard library. Python interpreters are available for many operating systems, allowing Python code to run on a wide variety of systems. CPython, the reference implementation of Python, is open source software and has a community-based development model, as do nearly all of its variant implementations. CPython is managed by the non-profit Python Software Foundation."""
Hint:  Assume that the first word is preceded by " "

a.	Build a dictionary where the key is a word and the value is the list of words that are likely to follow.
i.	E.g. Python --> [is, has, features, interpreters, code, Software]. In this example the words listed are likely to follow “Python”
b.	Given a word predict the word that’s likely to follow.

Code

```python
str1="""Python is a widely used high-level programming language for general-purpose programming, created by Guido van Rossum and first released in 1991. An interpreted language, Python has a design philosophy which emphasizes code readability (notably using whitespace indentation to delimit code blocks rather than curly braces or keywords), and a syntax which allows programmers to express concepts in fewer lines of code than possible in languages such as C++ or Java. The language provides constructs intended to enable writing clear programs on both a small and large scale .Python features a dynamic type system and automatic memory management and supports multiple programming paradigms, including object-oriented, imperative, functional programming, and procedural styles. It has a large and comprehensive standard library. Python interpreters are available for many operating systems, allowing Python code to run on a wide variety of systems. CPython, the reference implementation of Python, is open source software and has a community-based development model, as do nearly all of its variant implementations. CPython is managed by the non-profit Python Software Foundation."""

wordList = str1.split()
word = input("Enter a valid string: ")

mylist = []
if word in wordList:
  for i, e in enumerate(wordList):
    if word == e :
      mylist.append(wordList[i+1])
else:
  print(f'{ word } is not present in the string.')

print(f'{word} --> {mylist}')
```

Output

```bash
Enter a valid string: Python
Python --> ['is', 'has', 'interpreters', 'code', 'Software']
```

## Question 9
Below is the output of # show ip interface brief command on a router

Interface		IP-Address	OK? 	Method Status	Protocol
 
FastEthernet0/0	192.168.1.242	YES 	manual up	up 
FastEthernet1/0        unassigned	YES 	unset		down 
Serial2/0              	192.168.1.250	YES 	manual up	up 
Serial3/0              	192.168.1.233	YES 	manual up	up 
FastEthernet4/0        unassigned	YES 	unset  		down	
FastEthernet5/0        unassigned	YES        unset 		down

a.	Use regular expressions to extract and display Interface and method status for all the interfaces.
i.	E.g.  FastEthernet0/0, manual up

Code

```python
import re

string = '''Interface		IP-Address	OK? 	Method Status	Protocol
 
FastEthernet0/0	192.168.1.242	YES 	manual up	up 
FastEthernet1/0        unassigned	YES 	unset		down 
Serial2/0              	192.168.1.250	YES 	manual up	up 
Serial3/0              	192.168.1.233	YES 	manual up	up 
FastEthernet4/0        unassigned	YES 	unset  		down	
FastEthernet5/0        unassigned	YES        unset 		down
'''

print(re.findall("([a-zA-Z0-9/]+)\s+[0-9a-z.]+\s+[A-Z]+\s+([a-z]+)\s+([a-z]+)\s+.+", string))
```

Output

```bash
[('FastEthernet0/0', 'manual', 'up'), ('FastEthernet1/0', 'unset', 'down'), ('Serial3/0', 'manual', 'up'), ('FastEthernet4/0', 'unset', 'down')]
```

## Question 10
Given a number line from -infinity to +infinity. You start at 0 and can go either to the left or to the right. The condition is that in i’th move, you take i steps. In the first move take 1 step, second move 2 steps and so on. 
Hint: 3 can be reached in 2 steps (0, 1) (1, 3). 2 can be reached in 3 steps (0, 1) (1,-1) (-1, 2)

a) Find the optimal number of steps to reach position 1000000000 and -1000000000. 

Code

```python
import sys

def steps(source, step, dest):
  if (abs(source) > (dest)) :
    return sys.maxsize 

  if (source == dest):
    return step

  pos = steps(source + step + 1, step + 1, dest)
  neg = steps(source - step - 1, step + 1, dest)

  return min(pos, neg)
	
dest = 1000000000
print(f"No. of steps required to reach { dest }  is { steps(0, 0, dest) }")
```

Output

```bash
For 1000000000

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 6, in steps
  File "<stdin>", line 6, in steps
  File "<stdin>", line 6, in steps
  [Previous line repeated 995 more times]
  File "<stdin>", line 2, in steps
RecursionError: maximum recursion depth exceeded while calling a Python object

For -1000000000

No. of steps required to reach -1000000000  is 9223372036854775807
```
