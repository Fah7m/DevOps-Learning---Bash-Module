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

If statements
---

Condition in if statements are formed used comparison operators

Example of these operators are:

<img width="467" alt="image" src="https://github.com/user-attachments/assets/01afd711-0f72-4605-8cd8-7f4ba4feb595" />


an example of a simple if statement would be this 

<img width="550" alt="image" src="https://github.com/user-attachments/assets/8697cd8b-e581-4fd0-8c42-4c07597dc763" />

If statements become more powerful with logical operators such as these

```
&& = AND
|| = OR

```

These logical operators can be used as this 

```
#!/bin/bash

grade =95

if [ $grade -ge 90 ] && [ $grade -le 100]
then 
  echo "Excellent"
fi
```

Bash provides operates like the below to compare strings

```
== - meaning equals
!= - meaning not equals to
```

An example of this would be as follows:

<img width="554" alt="image" src="https://github.com/user-attachments/assets/e7459a47-4daa-4920-85b4-f9265d948eb3" />

^ that would then print out "Hello, Ahmed" as the condition is met with the name variable


Else and Elseif
----

The Else clause comes in when a condition is not false which gives you an alternative code block to execute when the initial condition is false

Here is how it would work.

![image](https://github.com/user-attachments/assets/656108e0-c4ae-4dd3-9eed-65f198e59f12)

In this case, the age is set to 15 meaning that if the age is not greater than 18 the output will be "You are not an adult!"

Elif allows us to add another condition if the first condition is false. This allows for multiple results to be printed 

![image](https://github.com/user-attachments/assets/fe278ad6-c679-4abb-95a1-b54a00d6e272)

In that example we can see that if the score is above 90 they get an "Excellent" and if they get above 80 they get a "Good". 

If none of those conditions are met then they get a "better Luck next time".

Nested If
---
Nested if statements allow us to create more complex decision making structures by embedding if statements within other if statements

These if statements make it possible for us to have conditions that are met and if one of those conditions are not met, then the user can't go through.

Example:

![image](https://github.com/user-attachments/assets/a2b1bd97-19f7-4e85-b393-6085eaaaaf33)

In this example we can see that the age is 18 and grade is 85. If the age is greater than 18 then they can move forward however their grade has to be higher than 

Benefits of Nested If:
- They allow the evaluation of multiple coniditons
- They enhance the flexibility and versatility of bash scripts


While loops
---
While loops allow you to execute a certain block of code whilst a certain condition remains true

These while loops are caled by doing the following 

![image](https://github.com/user-attachments/assets/fba86d11-6de0-4306-96d2-dfea40accd10)


While loops can also be used to process data from arrays or files, allowing you to automate tasks that involve iterative operations.

![image](https://github.com/user-attachments/assets/0dbe2e77-0e76-4015-8365-89a557d9479a)

In this example we see the array that is held in the fruits variable - (array meaning list)

The index value is set to 0 and we have done a while loop that iterates over the arrays in Fruits until it finishes. 

Within each iteration it will print out the current fruit and increments the index variable by one.

```
echo "Fruit: ${fruits[$index]}"
((index++))
done
```

This loop will continue until all the elements in the array are processed - e.g. this time there is only 3 fruits (apple, banana, orange) so it will go from 0,1,2,3 and since there isn't a 4th element in the array the while loop will exit.

To summarize this, while loops allow you to execute a block of code as long as the condition is true. This condition is evaluated before each iteration and the loop will continue until the condition becomes false.

These while loops are important for automating tasks and iterating data.


For Loops
---

For loops allow you to iterate over a sequence of values and perform repetitve tasks. Once again For loops are also powerful for automating tasks and processing data.

![image](https://github.com/user-attachments/assets/f5fa607b-221a-4919-8723-05552e6165e9

This example is similar to the while loops example but in this case the for loop iterates over each element in the fruits array which is set in the fruits variable at the top.

This loop then repeats over 3 times and prints out "Fruits: $fruit"

These loops can be used to iterate over a range of values using the sequence command by doing the below

![image](https://github.com/user-attachments/assets/b4be5830-eb46-41a4-aefa-415de11e324f)

The sequence command will generate a sequence of numbers from the first arguement which in this case is 1, up until the second argument which is 5.

The output of the command is then passed in as the input for the for loop and assigned to the variable number for each element in the sequence

The variable in the loop take on each value in the sequence and the code block between the do and done keyword is what's executed each time till the condition becomes false - Condition becomes false in this case when the loop is done until the number 5 which ends the for loop

For loops can be used with arrays, lists of values or ranges to automate tasks

Here is a another example of how you can do ranges without sequence 

```
for (( i=1; i<=5; i++ ))
do
echo "Number: $i"
done
```

So what's done here is the variable that is set is i which equals 1. Then the sequence is i being less than our equal to 5 and finally the variable i is then incremented each time so the number goes up in the sequence - ++ is the expressions used for adding one to the element


Break and Continue in loops
---

Break and Continue statements provide additional control within for and while loops allowing you to interrupt or skip iterations based on specific conditions.

The break statement will immediately exit the loop if the condition that is set is met.

![image](https://github.com/user-attachments/assets/52e4c3fc-3b2f-4e38-a39f-bd311ee5b8ae)

In this example the condition for the break statement is if the value of i is = to 3 then we will break the for loop and close the if statement - also a echo Number: $i for each number

The output will only be number 1 and 2 as it breaks at number 3

The continue statement will do the opposite as instead of breaking it will just continue on and skip over 3

![image](https://github.com/user-attachments/assets/5aae919f-644b-4641-9443-96e3be0c5378)


An example of a break statement in a while loop would be the below

![image](https://github.com/user-attachments/assets/cb55b913-8a91-47db-86af-9357ef134421)

The while true statement means that the loop will continue indefinitely unless the loop is broken

Then the value of count is incremented and echoed until count equals 4 and that's where the while loop is broken.

The output would go up to 3 and exit the loop

An example of a continue statement would be

![image](https://github.com/user-attachments/assets/552b595f-0126-4aa2-bd02-6dcd56d5d40c)

In the while condition we can see if count is less than 5 then the following codeblock in do is executed meaning that the loop will end once the count hits 5

In the do codeblock the condition that is set is if count is equal to 3 then we just increment it by one and continue one with the rest of while loop

Which the rest of the loop is just the count variable incremented and echoed
