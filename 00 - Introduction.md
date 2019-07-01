# Bash Scripting Knowledge Check
Bash is the default shell for most UNIX systems. Therefore, as a cyber warfare operator it will be necessary for you to understand Bash scripting.

This course will follow the outline below. Each section will have a basic lesson and then one or more knowledge checks per area. Answers can be found in the accompanying documents.

## Course Outline
01. Basics  
    - Variables  
    - Conditionals  
    - If Statement  
    - If / Else If / Else  
    - For Loop  
    - While Loop  

# Basics
### Variables

Example basic script using a variable:
```bash
#!/bin/bash
# A simple script to print a string
MY_STR = "Hello World!"
echo $MY_STR
```
The output will be:
```console
Hello World!
```

### Conditionals
The following conditionals can be used in bash:

| Description      | Numeric Comparison | String Comparison |
| ---------------- | ------------------ | ----------------- |
| less than        | -lt                | <                 |
| greater than     | -gt                | >                 |
| equal            | -eq                | =                 |
| not equal        | -ne                | !=                |
| less or equal    | -le                | N/A               |
| greater or equal | -ge                | N/A               |

0 -> True  
1 -> False

Example #1:
```bash
#!/bin/bash
string_a="UNIX"
string_b="GNU"
echo "Are $string_a and $string_b strings equal?"
[ $string_a = $string_b ]
echo $?
```
The output of that script is:
```console
Are UNIX and GNU strings equal?
1
```
Example #2:
```bash
#!/bin/bash
num_a=100
num_b=100
echo "Is $num_a equal to $num_b ?"
[ $num_a -eq $num_b ]
echo $?
```
The output of that script is:
```console
Is 100 equal to 100 ?
0
```

## Knowledge Check
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
    2.
    3.
2.
3.




### If Statement

```
#!/bin/bash
num_a=100
num_b=200
if [ $num_a -lt $num_b ]; then
    echo "$num_a is less than $num_b!"
fi
```

If / Else if / Else:
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
