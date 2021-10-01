### Domain: short-py.org


# tinier-py
A collection of tricks to help you code golfing with Python or to confuse your code reviewers.

I use these python tricks all the time when clashing in shortest mode on codingame or playing code golf. These are very useful. If you want to add another snippet, create a pull request. Also, it would be very nice to help sorting that unsorted stuff.


### collection of unsorted stuff

```py
print(str(1<2).lower())
```
can be written as
```py
print('ftarlusee'[1<2::2])
```
<hr />

```py
a=input()
b=input()
print(a+b)
```
can be written as
```py
I=input
a=I()
b=I()
I(a+b)
```
<hr />

```py
a=int(input())
b=int(input())
c=int(input())
```
can be written as
```py
a,b,c=map(int,open(0).read().split())
```
<hr />

```py
a==0
```
can be written as
```py
a<1
```
<hr />

```py
l1 = [1, 2, 3, 4, 5]

for i in range(len(l1)):
	if i != len(l1) - 1:
		val1 = l1[i]
		val2 = l1[i+1]
```
can be written as
```py
l1 = [1, 2, 3, 4, 5]

for val1, val2 in zip(l1, l1[1:])
```
<hr />

```py
print(str(a//b) + " " + str(b//a))
```
can be written as
```py
print(a//b,b//a)
```
<hr />

```py
import math
math.sqrt(int(input()))
```
can be written as
```py
int(input())**0.5
```
<hr />

```py
import math
a = float(input())

# checks for integer (1.0 = True, 1.2 = False)
print(math.floor(a) == math.ceil(a))
```
can be written as
```py
a=float(input())
print(a%1==0)
```
<hr />

```py
def isprime(number):
	...

a=int(input())
print(isprime(a))
```
can be written as
```py
a=int(input())
print([i for i in range(2,a)if(a%i<1)]==[]and a>1)
```
<hr />

```py
word = input()

print([c for c in word if c.isupper()])
```
can be written as
```py
import re
word=input()
print(re.sub('[^A-Z]','',word))
```
<hr />

```py
import math

a = float(input())
print(math.floor(a/3))
print(math.ceil(a/3))
```
can be written as
```py
a = float(input())
print(a//3))
print(-(a//3))
```
<hr />

```py
# optional decimal point
"""
1.0 = 1
1.4 = 1.4
"""
```
can be written as
```py
print("%g"%(my_float))
```
<hr />

```py
A = list(range(3))
```
can be written as
```py
*A=range(3)
```
<hr />

```py
list(map(...))
```
can be written as
```py
[*map(...)]
```
<hr />

```py
L = [1, 2, 3, 4]
a = L[-1]
```
can be written as
```py
L = [1, 2, 3, 4]
*_,a=L
```
<hr />

```py
L = [1, 2, 3, 4]
L.pop(0)
```
can be written as
```py
L = [1, 2, 3, 4]
_,*L=L
```
<hr />

```py
for x in range(a):
	for y in range(b):
		print(x, y)
```
can be written as
```py
for xy in range(a*b):
	x = xy//a
	y = xy%a
```
<hr />

```py
for x in range(10):
	print(1)
```
can be written as
```py
for x in range(10):
 print(1)
```
or even better as
```py
for x in range(10):print(1)
```
<hr />

```py
for x in range(3):
	print(x)
```
can be written as
```py
for x in 0,1,2:
	print(x)
```
<hr />

```py
for _ in range(10):
	print(1)
```
can be written as
```py
for _ in[1]*10:
	print(1)
```
<hr />

```py
print(', '.join(['A', 'B']))
```
can be written as
```py
print(*['A','B'],sep=', ')
```
<hr />

```py
print(x == 5 and y == 6)
```
can be written as
```py
print(x,y)==(5,6)
```
<hr />

```py
for _ in range(n):
	print(1)
```
can be written as
```py
exec('print(1);'*n)
```
<hr />

```py
print(sum(list(map(lambda e: e+1, [1, 2, 3, 4, 5, 6]))))
```
can be written as
```py
print(sum(map(int(1).__ad__,[1,2,3,4,5,6])))
```
<hr />

```py
print(" ".join(map(..., [0,1,2,3,4,5,6])))
```
can be written as
```py
print(*map(...,range(7)),sep=" ")
```
<hr />
