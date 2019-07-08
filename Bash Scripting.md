# Bash Scripting Knowledge Check
Bash is the default shell for most UNIX systems. Therefore, as a cyber warfare operator it will be necessary for you to understand Bash scripting.

This course will follow the outline below. Each section will have a basic lesson and then one or more knowledge checks per area. Answers can be found in the accompanying documents.

## Course Outline
1. Variables
0. Arithmetic
0. Comparisons and Operators
0. If Statements
0. If / Else If / Else Statements
0. For Loops
0. While Loops

### Variables

A variable is defined with '=', and there cannot be spaces between the variable name, equal sign, and value of the variable.  
Strings can be defined with single or double quotes:  
Single quotes: '\<text>' *fully* captures the text, meaning the text is taken as literal characters.  
Double quotes: "\<text>" *partially* captures the text, meaning the text will expand variables.  
A pound sign '#' begins a comment, which is not interpreted by Bash. These are simply human-readable notes.

**Example:**
```bash
#!/bin/bash
# A simple script to print strings
MY_STR='Hello World!'
echo $MY_STR
echo "My string is: $MY_STR"
echo 'My string is: $MY_STR'
```
**Output:**
```console
Hello World!
My string is: Hello World!
My string is: $MY_STR
```

There are also a number of special variables that Bash can use:
- $0 - The name of the Bash script
- $1 - $9 - The first 9 arguments provided to the Bash script
- $# - How many arguments were passed to the Bash script
- $@ - All the arguments supplied to the Bash script
- $? - The exit status of the most recently run process
- $$ - The process ID of the current script
- $USER - The username of the user running the script
- $HOSTNAME - The hostname of the machine the script is running on
- $SECONDS - The number of seconds since the script was started
- $RANDOM - Returns a different random number each time is it referred to
- $LINENO - Returns the current line number in the Bash script

We can save the output of a command to a variable like so: ```variable=$( <command> )```. This is known as command substitution.

> ## *Knowledge Check*
> ```bash
> #!/bin/bash
> MY_STR="Hi there!"
> echo 'My string is: $MY_STR'
> echo "My string is: $MY_STR"
> ```
> 1. What will be the first line output by this script?
> <!-- My string is: Hi there! -->
> 0. What will be the second line output by this script?
> <!-- My string is: $MY_STR -->
>
> ```./example_script 0 1 2```
> ```bash
> #!/bin/bash
> echo $0
> echo "Printing $3, $2, $1"
> echo $#
> ```
> 3. What will be the first line output by this script?
> <!-- ./example_script -->
> 0. What will be the second line output by this script?
> <!-- Printing 2, 1, 0 -->
> 0. What will be the third line output by this script?
> <!-- 3 -->

### Arithmetic
The operators +, -, \\\*, /, var++, var--, and % can be used to add, subtract, multiply, divide, increment, decrement, and modulus, respectively.

The command ```let``` evaluates an arithmetic expression and can be used to save the result to a variable.  

**Example:**
```bash
#!/bin/bash
# Demonstrate usage of let with arithmetic expressions
let a=5+4
echo $a # prints 9
let "a = 5 + 4" # quotes with let allows us to use spaces
echo $a # prints 9
let "a = $1 + 30" # recall $1 is the first argument provided to the script
echo $a # prints the result of $1 plus 30
```
**Output:**

Calling ```./example_script 9``` will produce the following:
```console
9
9
39
```
The command ```expr``` also evaluates an arithmetic expression but instead of saving to a variable it prints the answer.

**Example:**
```bash
#!/bin/bash
# Demonstrate usage of expr with arithmetic expressions
expr 5 + 4 # you don't use quotes with expr, and must have spaces
expr "5 + 4" # if quotes are used, expr simply prints the expression
expr 5+4 # if spaces are not used, expr simply prints the expression
expr 5 \* 4 # here, Bash requires an escape of the asterisk for multiplication
a=$( expr 5 + 4 ) # expr can be combined with command substitution
echo $a
```
**Output:**
```console
9
5 + 4
5+4
20
9
```

Double parentheses can also be used to evaluate an arithmetic expression, like ```expr```. This syntax can be combined with command substitution like so: ```variable=$(( <expression> ))```

Note, you cannot simply write a line like ```b=a+3``` in Bash like you can in other programming languages. Bash must be given a command to evaluate the expression with mechanisms like ```let```, ```expr```, or ```(( <expression> ))```. In fact, the error you will receive is ```command not found```.

**Example:**
```bash
#!/bin/bash
# Demonstrate usage of (( )) with arithmetic expressions
a=$(( 4 + 5 )) # the double parentheses evaluates the arithmetic expression
echo $a # print 9
a=$((3+5)) # with this syntax, we can omit the spaces and it still works
echo $a # prints 8
b=$(( a + $a )) # you can choose whether to use $ with a variable, either works
echo $b # prints 16
(( b++ )) # the double parentheses will evaluate this arithmetic expression
echo $b # prints 17
c=$(( 4 * 5 )) # here, Bash does not need to escape the asterisk for multiplication
echo $c # prints 20
```

**Output:**
```console
9
8
16
17
20
```

This is not truly arithmetic, but ```${#var}``` is extremely useful. It produces the length of the variable (its number of characters). For example, if ```a='Hello World'```, then ```${#a}``` is 11. If ```b=4953```, then ```${#b}``` is 4.

> ## *Knowledge Check*
> ```bash
> 
> ```


### Comparisons and Operators
Bash makes the Boolean comparison OR using double pipes '||' and AND using double ampersands '&&'.

The following conditionals can be used in bash. Note the different usage depending on whether you're comparing numbers or comparing strings.

| Description      | Numeric Comparison | String Comparison |
| ---------------- | ------------------ | ----------------- |
| less than        | -lt                | <                 |
| greater than     | -gt                | >                 |
| equal            | -eq                | =                 |
| not equal        | -ne                | !=                |
| less or equal    | -le                | N/A               |
| greater or equal | -ge                | N/A               |

### If Statements
Square brackets are a reference to the command ```test```. That command evaluates whatever is in the square brackets and exits with a status. A status of 0 means it exited with success; a status of 1 means it exited with failure. In other words, 0 -> True and 1 -> False.

<!-- If statements can be used to [[ evaluate ]] or test (( arithmetic )) -->

**Example:**
```bash
#!/bin/bash
# There are two ways to write an if statement:

if [<test>]; then
  echo "The test returned True"
fi


```

```bash
#!/bin/bash

```


```bash
#!/bin/bash
num_a=100
num_b=200
if [ $num_a -lt $num_b ]; then
    echo "$num_a is less than $num_b!"
fi
```



**Example:**
```bash
#!/bin/bash
string_a="UNIX"
string_b="GNU"
echo "Are $string_a and $string_b strings equal?"
[ $string_a = $string_b ]
echo $?
```
**Output:**
```console
Are UNIX and GNU strings equal?
1
```
**Example:**
```bash
#!/bin/bash
num_a=100
num_b=100
echo "Is $num_a equal to $num_b ?"
[ $num_a -eq $num_b ]
echo $?
```
**Output:**
```console
Is 100 equal to 100 ?
0
```


## *Knowledge Check*
Using this script, answer the following questions.

```bash
#!/etc/bash
my_name="Bash Lord"
echo "My name is $my_name"
num_a = 1000
num_b = 1001
echo "I know that $num_b is greater than $num_a"

```
1. What is the first line of output?
    1.
    1.
    1.
1.
1.



### If / Else if / Else:
```
#!/bin/bash
# elif statements
if [ $1 -ge 18 ]
then
echo You may go to the party.
elif [ $2 == 'yes' ]
then
echo You may go to the party but be back before midnight.
else
echo You may not go to the party.
fi
```
#### Loops:
For Loop:
```
#!/bin/bash
for i in 1 2 3; do
  echo $i
done
```
While Loop:
```
#!/bin/bash
counter=0
while [ $counter -lt 3 ]; do
    let counter+=1
    echo $counter
done
```
