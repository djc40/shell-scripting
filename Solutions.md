# Bash Scripting Knowledge Check Solutions

## Course Outline
1. Variables
0. Arithmetic
0. Comparisons and Operators
0. If Statements
0. If / Else If / Else Statements
0. For Loops
0. While Loops
0. Functions
0. Input
0. File Operations

## Variables

```bash
#!/bin/bash
MY_STR="Hi there!"
echo 'My string is: $MY_STR'
echo "My string is: $MY_STR"
```
1. What will be the first line output by this script?  
```My string is: Hi there!```

0. What will be the second line output by this script?  
```My string is: $MY_STR```

```./example_script 0 1 2```  
```bash
#!/bin/bash
echo $0
echo "Printing $3, $2, $1"
echo $#
```
3. What will be the first line output by this script?  
```./example_script```

0. What will be the second line output by this script?  
```Printing 2, 1, 0```

0. What will be the third line output by this script?  
```3```

## Arithmetic

```./example_script 2 3```
```bash
let "num_1 = $1 * $2"
echo $num_1
expr $1 \* $2
expr $1 * $2
num_2=$(( num_1 / $1 ))
echo $num_2
```
1. What will be the first line output by this script?
  - [ ] 2
  - [ ] 3
  - [X] 6
  - [ ] Error
0. What will be the second line output by this script?
  - [ ] 2
  - [ ] 3
  - [X] 6
  - [ ] Error
0. What will be the third line output by this script?
  - [ ] 2
  - [ ] 3
  - [ ] 6
  - [X] Error
0. What will be the fourth line output by this script?
  - [X] 2
  - [ ] 3
  - [ ] 6
  - [ ] Error

```bash
#!/bin/bash
expr $RANDOM % 100
```
5. What will this script output?  
`A random number between 0 and 100`

6. Write a script to convert a fahrenheit value to celsius, to the nearest integer. (Hint: pass the fahrenheit value to the script as a command line argument.) For a challenge, output the answer to 3 decimal places.

```bash
#!/bin/bash
# This script is one example solution to the problem
# It accepts a fahrenheit value and converts it to celsius
echo "$1 degrees fahrenheit is $(( ($1-32)*5/9 )) degrees celsius"
```
```bash
#!/bin/bash
# This script shows two solutions to the challenge problem
# It accepts a fahrenheit value and converts it to celsius
printf "$1 degrees fahrenheit is %.3f degrees celsius\n" $( awk "BEGIN {print ($1-32)*5/9}" )
printf "$1 degrees fahrenheit is %.3f degrees celsius\n" $( echo "($1-32)*5/9" | bc -l ) # bc must be installed
```

## Comparisons and Operators
```bash
#!/bin/bash
[ -z $1 ]
echo $?
```

1. What is the output if the script is called like so?:  
```./example_script Hello```
  - [X] 0
  - [ ] 1
  - [ ] Hello
  - [ ] No output
0. What is the output if the script is called like so?:  
```./example_script```
  - [ ] 0
  - [X] 1
  - [ ] Hello
  - [ ] No output

## If Statements
```bash
#!/etc/bash
num_a=1000
num_b=1001
if [ $num_a != $num_b ]
then
  echo "$num_a and $num_b are not the same"
fi
```
What is the output of this script?
  - [ ] 1000 and 1001 are not the same
  - [X] No output


## If / Else If / Else Statements
```bash
#!/etc/bash
if [ $1 -gt $2 ]
then
  echo "$1"
elif [ $2 -gt $1 ]
then
  echo "$2"
else
  echo "--"
fi
```
What does this script do?  
It prints the larger of the two numbers provided, or '--' if they are the same

## For Loops
```bash
#!/bin/bash
for val in {1..10}
do
  echo $val
done
```
1. What will be the first line output by this script?  
`1`
0. What will be the fifth line output by this script?  
`5`

```./example_script /usr```
```bash
#!/bin/bash
for entry in $(ls $1)
do
  echo $entry
done
```
3. What will be the first line output by this script?  
It depends on the OS distribution but probably bin
0. Briefly describe what this script is doing  
It prints out each entry in the given directory

## While Loops
```bash
#!/bin/bash
counter=5
while [ counter -gt 0]
do
  echo $counter
done
```
1. What will be the first line output by this script?  
`5`
0. What will be the fifth line output by this script?  
`5`; there is no decrement changing the counter so this will loop forever.

```bash
#!/bin/bash
counter=1
while [ $counter -lt 20]
do
  echo $counter
  if [ $(($counter % 2)) -eq 0]; then
    echo "even"
  fi
  let "counter = counter + 1"
done
```
3. What will be the fourth line output by this script?  
`3`
0. What is the sixth line output by this script?  
`even`

## Functions
```bash
#!/bin/bash
my_function() {
  if [ $# -ne 2 ]; then
    echo "Incorrect"
  else
    echo $(($1 + $2))
  fi
}

my_val=$(my_function 4 5)
echo "My first value is $my_val"
my_val=$(my_function 1 2 3)
echo "My second value is $my_val"
```
1. What is the first line of output of this script?
  - [ ] `My first value is 4`
  - [ ] `My first value is 5`
  - [ ] `My first value is 9`
  - [ ] `My first value is Incorrect`
0. What is the second line of output of this script?
  - [ ] `My second value is 1`
  - [ ] `My second value is 2`
  - [ ] `My second value is 6`
  - [ ] `My second value is Incorrect`

## Input

1. Write a simple script to collect a username and password from the user. Make sure the password is not visible as the user types it in.

```bash
#!/bin/bash
# This script is one example solution to the problem
echo Input your new credentials:
read -p "Username: " username
read -sp "Password: " userpass
echo
echo Thank you, $username, your credentials have been input.
```

2. Now, develop that script to ask for the password twice, confirming that the input was the same both times. Keep asking until the password has been input correctly. (Hint: make use of while loops, if statements, and user input.)

```bash
#!/bin/bash
# This script is one example solution to the problem
echo Input your new credentials:
read -p "Username: " username
passcorrect=0

while [ $passcorrect -eq 0]
do
  read -sp "Enter Password: " pass1
  echo
  read -sp "Confirm Password: " pass2
  echo
  if [ $pass1 == $pass2 ]
  then
    passcorrect=1
  else
    echo Those passwords did not match. Input again.
  fi
done
echo Thank you, $username, your credentials have been input.
```
