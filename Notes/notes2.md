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

**Set -u** stops the script from executing if there are uninitialized variables in the script

For example:
![image](https://github.com/user-attachments/assets/2f899c36-eeb6-4866-b784-0019cb8535f6)

We can see the script fails because variable X is not set.

![image](https://github.com/user-attachments/assets/db7b8901-eeaa-4783-bb93-fec1a262cc56)

In this example we can see the variables X and Y are set but W is not which still causes the script not to run. Set - u stops the script from running into potential problems due to missing data.

Best use case for Set -u would be for scipts that depend on certain variables being initialized 

**Set -x ** prints each command that will be executed in the terminal before it actually executes. This is useful for following the flow of your script.

![image](https://github.com/user-attachments/assets/ea909988-d59b-4a41-8a71-4207309fca21)

Set -x is very useful when troubleshooting scripts so you can precisely see where it is going wrong.

A combination of Set -x and Set +x is very useful when you want to debug a certain part of your script.

Example output would be this 
![image](https://github.com/user-attachments/assets/62c6ef78-681d-4226-9167-043f7fbbb78f)

**Set -eux** is simply a combination of e, u, and x.

This combo will execute the script, prints each command before execution and stops at the failing command.

Other set commands are:

**Set -o nounset** - equivalent to set -u which helps you catch undefined variables
**Set -o errexit** - same as set -e which exits the script if a non zero error code is returned (basically if the script has a error it wont run) - Also runs the script up to where it fails
**Set -o pipefail** - - this will cause a pipeline to fail if the last command in the pipleline has failed.
![image](https://github.com/user-attachments/assets/7c78100c-0f9a-4626-ad53-cf6f525ca4c1)

Here we see that a file is being cat'd which doesn't exist and then a pipe is used to grep a word in that fine. This set -o pipefail doesn't move on to the grep command because the first command in the pipe has failed.

Changing PATH variable permm
---

This variable is a critical system variable that specifies the directories where the shell should look for executable files.

Our own directories can be added to PATH when installing new software or want scripts to be available system wide.

Changes to PATH made in the terminal are temporary. To mae it permanent we add it to the ZHRC or BASHRC file 

```
echo "export PATH=$PATH:~/mydir" >> ~/.zshrc or bashrc
```

In this command we are appending to the zshrc or bashrc file and we are adding the export=blahblah line.

Any binaries or executables that the system finds in the directory, it will take as a binary that can be run system wide.

```
source ./zshrc
or
source ./bashrc
```

The source command will put the changes into effect.

Now that we have added a change to the PARTH variable where it looks into our directory, a simple file like a helloworld.sh which echos helloworld can be run system wide in any directory.

![image](https://github.com/user-attachments/assets/25468c85-be4f-40f4-943c-51712d4c32be)

Standard Env Variables
---

Here are sone standard environment variables that are already set in linux 

![image](https://github.com/user-attachments/assets/9879202a-e729-4495-8975-abd5287b50c2)

The PATH env variable will echo the executable paths and where the binaries are stored.

The LANG env variable will echo the default language being used.

![image](https://github.com/user-attachments/assets/c1e95af2-ae98-42ad-84bb-8f9896ea04c7)

These will echo user for LOGNAME, the type of shell being used e.g. bin/bash or /bin/zsh and the current working directory - the directory you're currently in.

Reading files 
---
Reading files is a important task in scripting, it allows us to access and extract information from various types of files.

