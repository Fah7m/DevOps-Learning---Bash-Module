This was a challenging level that required a lot of help from chatgpt to help debug errors and understand how to generate random lines into 5 different files.

My working script

```
#!/bin/bash

mkdir arena_boss
echo "Directory returned: $?"

cd ~/arena_boss
echo "cd returned: $?"

arena() {
        local dir

        dir=arena_boss

        while [ -z $dir ]
        do

                touch file1.txt file2.txt file3.txt file4.txt file5.txt
        echo "files returned $?"
                break
        done


# Loop through the 5 files
for file in file{1..5}.txt; do
    # Pick a random number of lines between 10 and 20
    lines=$(( ( RANDOM % 11 ) + 10 ))

    echo "Writing $lines lines to $file"

    # Generate random lines
    for i in $(seq 1 $lines); do
        echo "Line $i: $(head /dev/urandom | tr -dc 'A-Za-z0-9' | head -c 8)"
    done > "$file"
done
echo "writing files returned $?"

local file_number

file_numbers=$(ls -1 | wc -l | xargs)


if [[ "$file_number" =~ ^[0-9]+$ ]] && [ "$file_number" -eq 5 ]; then
        ls --sort=size -l
fi
echo "file_number returned: $?"

local file

file=$(echo file*.txt)

for f in $file; do
        if grep -q "victory" "$f"; then
                echo "victory found in $f"

                else
                echo "victory not found in $f"
                fi
        done
        echo "grep returned $?"
}

arena
```
