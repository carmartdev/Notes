
<span class="tag">Tags</span>:   [[Bash]] [[Terminal]] [[Scripting]] [[Coding]]

Created at 2024-10-18 21:10
<span class="tag">Status</span>: <span class="success">Done</span>
<span class="danger">Sources</span>: FreeCodeCamp

# BashScript

## What is bash?
- A shell language
- Bourne again shell
- Easy commands
- Lightweight and always available
- Is not mutually exclusive
- Basic knowledge makes big difference
## How to run a bash file
```shell
chmod u+x test.sh
```

## Basic bash file structure

```shell
#!/bin/bash
## This is a comment
MY_VARIABLE=somevalue
echo $MY_VARIABLE
## Returns: somevalue
```
## String Interpolation
```shell
echo "My variable: $MY_VARIABLE"
## Another kind of interpolation
echo Hello $MY_VARIABLE wellcome to HELL
```

## Taking Inputs
```shell
echo What is your name?
read NAME
echo Hello $NAME
```

## Positional Arguments
Commands can take in arguments at a specific position, counting from one(0 is reserved for the shell)

```shell
echo hello AMIR!
# ^    ^     ^
# |    |     | 
#[0]  [1]   [2]
```

### Example:
```shell
echo Say hello to $1 $2
## Output:
## ./PA.sh Ur MOM
## Say hello to Ur MOM
```

## Piping
Sends command output to another one

### Example:
```shell
echo Hello there | grep there
```
*Output*:
Hello <span class="danger">there</span>

## Output redirection
- `>` symbol to write to a file
- `>>` to append to a file

```shell
echo HELLO > hell.txt
echo HELL >> hell.txt
## $ man hell.txt
## $ HELLO HELL
```

### Word Count and Output as Input
```shell
wc -w hello.txt
## Output: 7 hello.txt
wc -w < hello.txt
```

### Appending multiple lines to input with EOF
```shell
cat << EOF
> Hello
> How are you?
> EOF
Hello
How are you?
```

### <<<
```shell
wc -w <<< "Hell for UrMOM"
## Output: 3
```

## Test Operators
```shell
[hello = hello]
echo $?
# 0 True
```
```shell
[1 = 0]
echo $?
# 1 False
```
```shell
[1 -eq 1]
echo $?
# 0 True
```

## Conditionals
### If
```shell
# ${1,,} gets the first command line argument
if [${1,,} = Amir]; then
	echo "Hello Amir, How are you?"
```
### Elif
```shell
elif [${1,,} =]; then
	echo "Enter your name!"
```
### Else
```shell
else
	echo "Sorry I don't know you :/"
```
### End If
```shell
fi ## Ends the if statement
```
### Case statement
Better than if/elif/else when:
- Checking for multiple values
- Is easier to read
```shell
case ${1,,} in
	Amir)
		echo "Hello Amir, How are you?"
	help)
		echo "Enter your name!"
	*) ## Like the default in C
		echo "Sorry I don't know you :/"
esac ## Ends case
```

## Arrays (lists)
```shell
MY_FIRST_LIST=(1 2 3 4 5 6)
echo $MY_FIRST_LIST
## 1
echo ${MY_FIRST_LIST[@]}
# 1 2 3 4 5 6
echo ${MY_FIRST_LIST[1]}
## 2
```

## For loop
```shell
for item in ${MY_FIRST_LIST[@]}; do echo $item; done
## 1
## 2
## 3
## 4
## 5
## 6
```

## Functions
```shell
#!/bin/bash

showuptime(){
	echo Hello $1
	local up=$(uptime -p | cut -c4-) ## variables are global by default
	local since=$(uptime -s)
	cat << EOF
----------------
Uptime: $(up)
Since: $(since)
----------------
EOF
}
showuptime Amir
##          ^
##          |
## [this is the $1 argument]

## Output:
## Hello Amir
##----------------
## Uptime: 4 hours, 36 minutes
## Since: 2024-10-18 18:05:26
##----------------
```

## Exit Codes
```shell
showname(){
	echo hello $1
	if [ ${1,,} = Amir ]; then
		return 0
	else
		return 1
	fi
}
showname $1
if [ $? = 1 ]; then
	echo "Someone uknown called the function"
fi
```

## [[AWK]]
```shell
## test.txt: one 2 3
awk '{print $1}' test.txt
## one
## test.txt: one, 2, 3
awk -F, '{print $1}' test.csv
echo "One 2 3 4 5" | awk '{print $5}'
## 5
echo "One 2 3 4 500" | awk '{print $5} | cut -c2'
## 5
echo "One 2 3 4 500" | awk '{print $5} | cut -c2-'
## 500
```

## [[SED]]
```shell
sed 's/fly/grasshopper/g' test.txt
## replaces grasshopper with fly
sed -i.ORIGINAL 's/fly/grasshopper/g' test.txt
## makes a backup file
```


# References
