# Bash Scripting Knowledge Check Solutions

## Course Outline
1. Variables
0. Arithmetic
0. Comparisons and Operators
0. If Statements
0. If / Else If / Else Statements
0. For Loops
0. While Loops

### Variables

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

### Arithmetic

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
<!-- 6 -->
  - [ ] 2
  - [ ] 3
  - [X] 6
  - [ ] Error
0. What will be the second line output by this script?
<!-- 6 -->
  - [ ] 2
  - [ ] 3
  - [X] 6
  - [ ] Error
0. What will be the third line output by this script?
<!-- Error -->
  - [ ] 2
  - [ ] 3
  - [ ] 6
  - [X] Error
0. What will be the fourth line output by this script?
<!-- 2 -->
  - [X] 2
  - [ ] 3
  - [ ] 6
  - [ ] Error

```bash
#!/bin/bash
expr $RANDOM % 100
```
5. What will this script output?  
```A random number between 0 and 100```

### Comparisons and Operators
```bash
#!/bin/bash
[ -z $1 ]
echo $?
```
1. What is the output if the script is called like so?:  
```./example_script Hello```
<!-- 0 -->
  - [X] 0
  - [ ] 1
  - [ ] Hello
  - [ ] No output
0. What is the output if the script is called like so?:  
```./example_script```
<!-- 1 -->
  - [ ] 0
  - [X] 1
  - [ ] Hello
  - [ ] No output

### If Statements
```bash
#!/etc/bash
num_a=1000
num_b=1001
if [ $num_a != $num_b ]
then
  echo "$num_a and $num_b are not the same"
fi
```
1. What is the output of this script?
<!-- nothing -->
  - [ ] 1000 and 1001 are not the same
  - [X] No output


### If / Else If / Else Statements
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

### For Loops



### While Loops
