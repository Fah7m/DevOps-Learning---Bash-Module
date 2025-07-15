This was a challenging level that required a lot of help from chatgpt to help debug errors and understand how to generate random lines into 5 different files.

My working script

<img width="637" height="949" alt="image" src="https://github.com/user-attachments/assets/8184c792-9973-46e7-8d74-5fedacccfc1e" />


Important takeaways from this 
---

Firstly the script writing was very messy and I stuffed everything into one function which I think is not the best idea in this case.

I also echo'd the exit code from each part of the script a bunch of times to see try and debug - $? 

Needed a lot of assistance from chatgpt for the generating random lines into files 

First part 
---
➤ for file in file{1..5}.txt; do
✅ Loops over 5 filenames:

file1.txt

file2.txt

file3.txt

file4.txt

file5.txt

➤ lines=$(( ( RANDOM % 11 ) + 10 ))
✅ Generates a random number between 10 and 20:

RANDOM % 11 → gives 0–10

add 10 → results in 10–20

Examples:

10

12

17

So each file will have a random number of lines.

➤ for i in $(seq 1 $lines); do
✅ Loops from 1 → $lines to generate that many lines.

For example, if $lines = 15:

i = 1

i = 2

...

i = 15

➤ How Random Text Works
✅ head /dev/urandom → grabs raw random bytes.

✅ tr -dc 'A-Za-z0-9' → deletes everything except:

uppercase letters A–Z

lowercase letters a–z

numbers 0–9

✅ head -c 8 → limits it to 8 characters.

➤ done > "$file"
✅ Redirects all output of the inner loop into one file.

So instead of writing line by line separately, the loop’s entire output goes into $file.


✅ What It Does Not Do
🚫 This script does NOT:

insert the word “victory” in any file

choose one “winner” file

perform any search for words afterward

It simply creates random files with random contents.

✅ How to Add “Victory”
If you want to add a “victory” line randomly in one file, you’d have to:

✅ randomly choose one file:
```
victory_file=file$(( ( RANDOM % 5 ) + 1 )).txt
```

✅ randomly choose a line number within that file:

```
victory_line=$(( ( RANDOM % lines ) + 1 ))
…and write “victory” on that line.
```
