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

Here, we take a list of numbers from `addition.in`, seperated by commas, and print its sum in `addition.out`. Here's the solution I wrote;
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

Here, again, we take a list of numbers, seperated by commas, and print the message accordingly i.e.<br/>
`hi` if the number is 0-50 (inclusive)<br/>
`hey` if the number is 51-100 (inclusive)<br/>
`hello` otherwise<br/>
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
