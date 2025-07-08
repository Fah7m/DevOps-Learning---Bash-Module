BASH
---
Second section for my notes - this is where I'll have the videos from 21 and above notes on here.

Piping 
--

Piping allows us to pass the output of one command as an input to another.

![image](https://github.com/user-attachments/assets/841ea3ec-2517-4311-8d9b-0fb46fed19f0)

In this example we have the function get file count which two variables are called, directory which takes a parameter ($1) and file count.

File count variable is set to list (ls) whatever parameter is passed into the directory variable and a pipe is used to give a word count 

```
=$(ls "$directory" | wc -l)
```

Then a echo is printed out containing the output from the directory variable and file_count variable

Finally the function is called and a parameter is passed for the directory variable and the output is below

![image](https://github.com/user-attachments/assets/7f8569ab-068f-4fea-8c5e-8e9eec6c182c)

So first the directory is printed which is what's passed as the end of the function, and the file count variable is printed which is the number of files in said directory

Here is another way the piping can be used

![image](https://github.com/user-attachments/assets/1ddfe9d6-9917-43c9-9157-11645740edb6)

What we have here is the search logs function and inside it we have the search_term variable set to take a parameter "$1" that is passed into the function which is done at the end

We have the grep command to search for the parameter that is passed in the log.txt file.

Then we have the awk command which is used to analyze and process text files in Linux - we have it print out the column in the 5th position which is the message of the log

![image](https://github.com/user-attachments/assets/02ea35e5-fd4e-4606-8cc5-5f3c24dce251)

This is the 5th coloumn in the log file but it can be changed to print out whichever column.

Finally in that script the search logs function is called and the PASS messaged is parsed into the search_Term variable which gives us the output

![image](https://github.com/user-attachments/assets/e6c2cd22-cca0-4975-8e4e-17982f3d6fe2)


Error handling intro
---

Error handling is important to writing robust reliable scripts.

This is basically foreseeing where things can go wrong and taking an appropriate measure to handle those situations rather than letting the scripts crash or continue with errors.

![image](https://github.com/user-attachments/assets/4638ea2b-ca30-447d-9dad-f9f3874319d6)

In this example we have variables set and those variable are then divided by each other however, nothing can be divided by 0 so this would cause an error in script and crash it.

What we do in place is set a if statement which checs if the value of the variable is 0, if so a message is echoed and a exit code of 1 is set.

This prevents the script from crashing and allows for a error message to return instead.

Here is an example of error handling without exit codes 

![image](https://github.com/user-attachments/assets/576d440a-5e30-46d6-b1ca-9c776c95214e)

So we set in place a variable with a nonexistent file and our if statements searches if the value in the variable FILE exists with the -f parameter.

If it doesn't exist a error message is returned - simples

Exit codes 
---

Whenever a command or script ends, it returns an exit code to the system which is a numerical value.

This value determines whether the script has completed sucessfully or not - exit code 0 indicates sucess and anything else indicates an error

![image](https://github.com/user-attachments/assets/c0cdbbb8-f20c-44ca-9dd9-308bfbdcba20)

This example checks if the command git exists and discards the error message into dev null 
```
>2>/dev/null
```
Then the if statement is set to check if the exit code is not equal to 0 then a message is echoed to install git - exit 1 giving us a errored exit code now

Else a sucessfully error message is echoed.

**Set -e** stops the script from executing any command if a non zero exit code is returned - so script ends if there is a error

![image](https://github.com/user-attachments/assets/88c2b717-520e-4ac2-b85c-9ce1f71f6616)

Anything after the error in the script will not run - there are some exit codes that are non zero which are indicative of errors 

Set -e wouldn't be used in cases where you want a non zero exit code and the script to carry on.



