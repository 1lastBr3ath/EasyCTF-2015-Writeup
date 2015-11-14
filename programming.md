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
open('math-class.out','w').write(str(abs(result))+'\n')
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

EasyCTF Day - 55 points 
----
EasyCTF started on November 3rd, 2015 this year. Find the position where the numerical representation of the month and day of this date `1103` is first found within pi. Use any language you'd like! The flag is the position of the first digit of the date within pi, where 3 is the first digit and the decimal point `.` is not considered a position.

**Hint**:
First you have to find a way to generate some digits of pi.

I solved it differently, using JavaScript. I Googled for *digits of pi*, visited a [site](http://www.geom.uiuc.edu/~huberty/math5337/groupe/digits.html), and extracted the `indexOf` **1103** using `Developer console`.<br/>
The query I used was;
```js
document.body.innerText.match(/3\.14.*?1103/).toString().replace(/\s/g,'').replace('.','').indexOf('1103')+1;
```
Flag: `easyctf{3494}`

I, later, found a [site](http://www.angio.net/pi/digits.html) that does it without any effort.

------------

Looking for Letters - 65 points
-------------
Use the programming interface to complete this task.

Input: A string containing alphanumeric characters.
Output: A string containing only the letters of the input.

Read the input from a file called `looking-for-letters.in` that's in the current working directory, and then write your output to a file called `looking-for-letters.out`.

**Hint**:
If you need help, try looking at the Python Tutorial in the Learn section!

Here, we take a `string` containing alphanumeric characters from `looking-for-letters.in`, and print `string` containing letters only to `looking-for-letters.out`. For this, I checked if the ordinal value of each character falls under `65 - 90` or `97 - 122`, which covers all, small as well as capital letters.<br/>
Here's the solution I wrote;
```python
chars = open('looking-for-letters.in','r').read()
tmp = []
for c in chars:
  if ord(c) in range(65,90) or ord(c) in range(97,122):
    tmp.append(c)
open('looking-for-letters.out', 'w').write(''.join(tmp)+'\n')
```
**Sample Input & Outpu**:
```zsh
$cat looking-for-letters.in 
1234qwert1234asdf
$python looking-for-letters.py
$cat looking-for-letters.out 
qwertasdf
```
Flag: `easyctf{filtering_the_#s_out}`

-------

String Change - 70 points 
-------
Use the programming interface to complete this task. Given an array of 5 numbers, change every nth character, with n being the value of the first number of the array and the first letter of the string as the 1st character, of a string and move its value up by one (a turns into b, z turns into a). Repeat this for the rest of the numbers of the array and return the changed string. Do this for all the strings. Be careful to keep the original capitalization!

For example: `[2,3,7,5,4]` and `oTerNmIWxGqaaV` would become `oUftOoJYyIqdaX`

ID: `string-change`
Input: Read the input from a file called `string-change.in` that contains a string of: a list of 5 numbers separated by commas followed by a linebreak, and then a string of random characters.
Output: The string changed according to the values in the list, written to a file called `string-change.out`.

**Hint**:
First, look into string splitting, and the `ord()` and `chr()` functions!

It took me long enough to solve, because I didn't understand the question clearly. When it says, '**change every nth character**', it means every nth i.e. if `n=2`, every multiples of `2` i.e. `2, 4, 6, 8` and so on. And, if a number repeats, increment it accordingly. In the example, 4th character, `r` was incremented to `t`, because it was, first, incremented as multiples of `2`, and second by `4` in the list. If you understand it clearly, it's quite straightforward.<br/>
Here's the solution I wrote;
```python
ip = open('string-change.in','r').readlines()
chars = list(ip[1].strip('\n'))
nums = map(int, ip[0].strip('\n').split(','))
i = None
for num in nums:
  i = num-1
  while i <= len(chars):
    if chars[i] == 'z': chars[i] = 'a'
    elif chars[i] == 'Z': chars[i] = 'A'
    else: chars[i] = chr(ord(chars[i])+1)
    i += num
open('string-change.out','w').write(''.join(chars)+'\n')
```
**Sample Input & Output**:
```zsh
$cat string-change.in 
20,2,11,12,19
ROqcrLmPZKxByDVVbCKojHSaOeQmrX
$ python string-change.py 
$ cat string-change.out 
RPqdrMmQZLyDyEVWbDLqjJScOfQnrY
```
Flag: `easyctf{changing_things_up_once_in_a_while_is_gooood_for_you}`

-----------

Oink - 85 points 
-------
Use the programming interface to solve this problem.

Pig Latin is a "secret" language in which English words are changed to sound foreign. Its rules are pretty simple:

    If the English word begins with a vowel, add "yay" to the end.
    If the English word begins with a consonant, move the first letter to the end and then add "ay".

For example, "Apples are Delicious" becomes "Applesyay areyay eliciousDay". Note: if you know a version of Pig Latin that uses a variation of rules different from the above rules, please use the above rules for this problem.

Your job is to translate English input to Pig Latin output. For this exercise, keep capitalized letters capitalized, even when they are moved.

ID: `piglatin1`
Input: A sentence in English.
Output: The translation in Pig Latin.

Read the input from a file called `piglatin1.in` that's in the current working directory, and then write your output to a file called `piglatin1.out`

**Hint**:
Words are defined as separated by spaces. :)

The solution is also straightforward,<br/>
\- we add 'yay' to the end if the word begins with vowel, else 
\- we move the first letter to the end, and add 'ay'<br/>
Here's the solution I wrote;
```python
words = open('piglatin1.in', 'r').read().split()
vowels = ['a','e','i','o','u','A','E','I','O','U']
pl = []
for c in words:
  if c[0] in vowels: pl.append(c+'yay')
  else: pl.append(c[1:]+c[0]+'ay')
open('piglatin1.out', 'w').write(' '.join(pl)+'\n')
```
**Sample Input & Output**:
```zsh
$cat piglatin1.in
I celebrate myself and sing myself
$python piglatin1.py
$cat piglati1.out
Iyay elebratecay yselfmay andyay ingsay yselfmay
```
Flag: `easyctf{atinl4y_easyyay_3noughyay_orfay_ayay_1gpay!}`

-----------

Oink Oink - 115 points
-------
Use the programming interface to solve this problem.

Now that we know how to convert from English to Pig Latin, can we reverse the translation? Given a sentence in Pig Latin, reverse it and try to find the original English text.

Be careful to note that if a Pig Latin word is capitalized, like "Arispay", the original English word is "Paris" rather than "pAris". Case counts!

ID: `piglatin2`
Input: A sentence in Pig Latin.
Output: The translation in English.

Read the input from a file called `piglatin2.in` that's in the current working directory, and then write your output to a file called `piglatin2.out`

**Hint**:
Work backwards! You'll probably need the `chr()` and `ord()` functions! Also, string splicing is pretty cool in Python ;)

It was almost similar to previous one, except in case of capitalization. There, it confused me for a moment.
Here's the solution I wrote;<br/>
```python
words = open('piglatin2.in', 'r').readline().split()
en = []
for word in words:
  if word[-3:] == 'yay': en.append(word[:-3])
  else:
    if ord(word[0]) in range(65,90):
      en.append(chr(ord(word[-3:-2])-32) + word[:-3].lower())
    else:
      en.append(word[-3:-2] + word[:-3])
open('piglatin2.out', 'w').write(' '.join(en)+'\n')
```
**Sample Input & Output**:
```zsh
$cat piglatin2.in
Iyay elebratecay yselfmay andyay ingsay yselfmay
$python piglatin2.py
$cat piglatin.out
I celebrate myself and sing myself
```
Flag: `easyctf{th0se_pesky_capit4ls_were_a_pa1n,_weren't_they?}`

------------

Obfuscated - 400 points 
-------
How good are you at reading Python? Put your Python skills to the test by finding the password that passes this check: [obfuscated.py](https://www.easyctf.com/static/problems/obfuscated/obfuscated.py)

Note: `easyctf{}` formatting is not required for this problem.

**Hint**:
Note: there may be multiple correct answers. The grader runs the same code that's in the given file.

This, to my knowledge, was/is not working properly. I went through the program thoroughly, and since I didn't get the complete flag, I, in order to view what it has to say given the wrong input, entered the string `canary`. In, other problems, it was giving a hint, kind of, but it accepted it as a flag instead. Tough it says, 'There may be multple correct answers', but according to the program given, a correct answer must of be 25 characters.
Anyway, here's my analysis of the program;<br/>
