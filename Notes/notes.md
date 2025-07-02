BASH
---
Key points for BASH:
Every script must have a shebang declared at the top - this line allows you to specify different types of scripts or interpreters e.g. #!/usr/bin/python3 to run python.
```
#!/bin/bash
```

To run a script you must first make it executable by running the below
```
chmod +x myscript.sh
```

To run the script you can do either of the following 

```
./myfirstscript.sh
```
or 
```
sh script.sh
```
To end this first part off the shebang line specifies the interpreter or shell that handles the script. It enables consistent execution of scripts across different environments.

--
Adding comments in the script are important and written by doing the following:

```
### this line is a commenct
```

To add Multi line comments you do the following:
```
: '
This is a multiline comment
'
```

Running scripts from anywhere
-----
A script can be run from anywhere by moving it into the /usr/local/bin directory as that is a $PATH directory

To move the script there do 

```
sudo mv greet.sh /usr/local/bin/greet
```

Here the name is changed and it has moved into that directory.

You will also need to make it executable by doing 
```
chmod +x /usr/local/bin/greet
```

Writing Variables 
---
You only add " when the variable is a string for example

```
greeting="hello world"
```

And you dont use the " when its not a string e.g.

```
count=42
```

An array is written in a variable by the following

```
fruits=("apple", "banana", orange")
```

Parameters 
----
Bash scripts can receieve input values known as parameters or arguments from the command line when they are executed.

This allows for the script to be customisable and make it more flexible

An example of this would be the following

```
!#/bin/bash

echo "Parameter 1: $1
echo "Parameter 1: $2
echo "Parameter 1: $3
```

Then the script can be run as ./script.sh and the return value would be the following.

<img width="208" alt="image" src="https://github.com/user-attachments/assets/e3931cc0-1388-4b88-8d04-0562f09bf698" />

All parameters can be passed by doing the following

<img width="167" alt="image" src="https://github.com/user-attachments/assets/f2a438e7-3f2a-4f32-b85b-f1dd99c9fc79" />

This will then return all the parameters that were parsed in one row as below

<img width="159" alt="image" src="https://github.com/user-attachments/assets/394f232d-03d1-452d-9c95-36f2976e7be0" />

To finish this off, parameters can be passed after the script name as show previously and inside the script they can be parsed with eith $1, $2 and so on based on their position

The special variable $@ can be used to access all the parameters.


Arithetic expansion
----

In simple terms, arithmetic expansion allows for us to do calculations such as the following.

```
#!/bin/bash

num1=5
num2=10

result=$((num1 + num2))

echo "The sum of $num1 and $num2 is: $result"

```

Another way this can be used is as follows

<img width="529" alt="image" src="https://github.com/user-attachments/assets/16e96829-aa40-4b27-9e4e-e47256dce814" />


Parameters and arith expansion
---

This is a good combination to speed up the process and a sense of automating your script.

The combination of both would look like this

```
length="$1"
width="$2"

area=$((length * width))
perimeter=$((2 * (length + width)))

echo "Rectangle area: $area"
echo "Rectanle perimeter: $perimeter"

```

In this above script we have used the previous arithmetic expansion but have now added the two parameter placeholders $1 and $2

This means that when the script is being run, we can now pass 2 numbers in the terminal to give us an answer for the calculation.

```
./arithmetic.sh 8 5

Rectangle area: 40
Rectangle permiter: 26"

```








