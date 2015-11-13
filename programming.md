Programming
-----------

Hello World! - 20 points
-----------
Use the programming interface to complete this task. Print the line `Hello, EasyCTF!` to a file called `hello-world.out`. For this problem and for future problems, **make sure your program ends with a newline**. Good luck!

**Hint**:
If you're really stuck, contact one of the mods on the [chat](https://www.easyctf.com/chat), or check out our [video tutorial](https://www.youtube.com/watch?v=GP1ZfzRSclQ)!

I don't assume this being a problem. It's, kind of, way to welcome us for programming challenges, I guess.<br/>
The problem is straightforward, we need to write a program that prints the message `Hello, EasyCTF!` to a file name `hello-world.out`.<br/>
I prefer `python` over `Java`, and here it is;
```python
open('hello-world.out','w').write('Hello, EasyCTF!\n')
```

Flag: `easyctf{welc0me_two_easyCtf}`

------------

Sum It! - 30 points
---------
Use the programming interface to complete this task. You'll be given a list of numbers.

Input: A list of numbers, separated by commas.
Output: The sum of the numbers.

Read the input from a file called `addition.in` that's in the current working directory, and then write your output to a file called `addition.out`.

**Hint**:
If you need help, try looking at the Python Tutorial in the Learn section!

Here, we take a list of numbers from `addition.in`, separated by commas, and print its sum in `addition.out`.<br/>
Here's the solution I wrote;
```python
nums = open('addition.in', 'r').read().split(',')
sum = 0
for num in nums:
  sum += int(num)
open('addition.out', 'w').write(str(sum)+'\n')
```

**Sample Input & Output**:
```zsh
$cat addition.in 
1,2,3,4,5,6,7,8,9
$python addition.py
$cat addition.out 
45
```
Flag: `easyctf{'twas_sum_EZ_programming,_am_I_rite?}`

--------------

If Logic - 30 points 
--------
Use the programming interface to complete this task. You'll be given a list of numbers.

Input: A list of numbers, separated by commas.
Output: Print `hi` if the number is 0-50 (inclusive), `hey` if the number is 51-100 (inclusive), and `hello` if anything else. Each greeting should have a linebreak after it.

Read the input from a file called `if-logic.in` that's in the current working directory, and then write your output to a file called `if-logic.out`.

**Hint**:
If you need help, try looking at the Python Tutorial in the Learn section!

Here, again, we take a list of numbers, separated by commas, and print the message accordingly i.e.<br/>
\- `hi` if the number is 0-50 (inclusive)<br/>
\- `hey` if the number is 51-100 (inclusive)<br/>
\- `hello` otherwise<br/>
Here's the solution I wrote;
```python
nums = open('if-logic.in', 'r').read().split(',')
msg = ''
for num in nums:
  if int(num) in range(0,51): msg += 'hi\n'
  elif int(num) in range(51,101): msg += 'hey\n'
  else: msg += 'hello\n'
open('if-logic.out', 'w').write(msg)
```
**Sample Input & Output**:
```zsh
$cat if-logic.in 
4,7,13,62,71,34,45
$python if-logic.py
$cat if-logic.out 
hi
hi
hi
hey
hey
hi
hi
```
Flag: `easyctf{is_it_hi_or_hey_or_something_else}`

-------------------------------------------

Can You Even??? 40 points 
-----------
Use the programming interface to complete this task. You'll be given a list of numbers.

Input: A list of numbers, separated by commas.
Output: The number of even numbers.

Read the input from a file called `can-you-even.in` that's in the current working directory, and then write your output to a file called `can-you-even.out`.

**Hint**:
If you need help, try looking at the Python Tutorial in the Learn section! Perhaps you should try looking into the modulo (%) operator. 

Here, we take a list of numbers, separated by commas, from `can-you-even.in`, and print the number of even numbers to `can-you-even.out`.<br/>
Here's the solution I wrote;<br/>
```python
nums = open('can-you-even.in', 'r').read().split(',')
count = 0
for num in nums:
  if int(num)%2 == 0: count+=1
open('can-you-even.out', 'w').write(str(count)+'\n')
```
**Sample Input & Output**:
```zsh
$cat can-you-even.in 
1,2,3,4,5,6,7,8,9
$python can-you-even.py
$cat can-you-even.out 
4
```
Flag: `easyctf{?v=8ruJBKFrRCk}`

-----------

Math Class - 50 points 
----------
Use the programming interface to complete this task. You'll be given a math expression, such as `add 1 2` or `subtract 5 3`, where you will perform the operations `1+2` and `5-3`, respectively.

ID: `math-class`
Input: An expression in the form of `operation operand1 operand2`, separated by spaces. Read input from `math-class.in`.
Output: The **absolute** value of the evaluated expression. Your output should always be a positive integer.

There are only 2 different possible operations, addition and subtraction, and all operands will be integer values between 1 and 1000. As always, remember to end your program with a newline.

**Hint**:
Two very useful functions are int() and split(). Read about them in the documentation.

Here, we take a mathematical expression in English form, as in `add 1 2`, separated by spaces, from `math-class.in`. Then, evaluate the expression, and print its absolute value in `math-class.out`.
Here's the solution I wrote;
```python
exp = open('math-class.in', 'r').read().split()
op1 = int(exp[1])	
op2 = int(exp[2])
if op1 in range(1,1000) and op2 in range(1,1000):
    if exp[0] == 'add': result = op1 + op2
    elif exp[0] == 'subtract': result = op1 - op2
open('math-class.out','w').write(str(abs(result))+"\n")
```

**Sample Input & Output**:
```zsh
$cat math-class.in 
add 45 7
$python math-class.py
$cat math-class.out 
52
```
Flag: `easyctf{have_y0u_had_enough_of_math_in_sk0ol_yet}`

----------

Sort-of Easy - 50 points 
-------
Use the programming interface to complete this task.

Input: A list of numbers, separated by commas. Ex: `3,28,9,17,5`
Output: The list sorted from largest to smallest, separated by commas. Ex: `28,17,9,5,3`

Read the input from a file called `sorting-job.in` that's in the current working directory, and then write your output to a file called `sorting-job.out`.

**Hint**:
I wonder if there is a handy sort function for this?

There might be a handy sort function, indee, but since I'm not that familiar with python, I did it my way. Here, we were to take a list of numbers, separated by commas, from `sorting-job.in`, and print it in descending order to `sorting-job.out`.
Here's the solution I wrote;
```python
nums = open('sorting-job.in','r').read().split(',')
nums = map(int, nums)
tmp = sorted(nums,None,None,True)
open('sorting-job.out','w').write(str(tmp).strip('[]').replace(' ','')+'\n')
```

**Sample Input & Output**:
```zsh
$cat sorting-job.in 
19,23,79,90,57,72,81,49,85,20
$python sorting-job.py
$cat sorting-job.out 
90,85,81,79,72,57,49,23,20,19
```
Flag: `easyctf{sorting_is_as_easy_as_3_2_1!}`

---------

