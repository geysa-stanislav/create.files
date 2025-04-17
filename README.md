# create.files
Write a Bash script based on the following requirements
#!/bin/bash

# Your name to use as the file prefix
name="Joao"  # <-- Replace with your own name

# Find the highest existing file number (e.g., Joao25, Joao50, etc.)
# It searches for files like Joao1, Joao2, ..., and gets the highest number
last_number=$(ls ${name}[0-9]* 2>/dev/null | grep -oP "${name}\K[0-9]+" | sort -n | tail -1)

# If no files are found, start from 0
if [ -z "$last_number" ]; then
    last_number=0
fi

# Create the next 25 files
for i in $(seq 1 25); do
    new_number=$((last_number + i))
    touch "${name}${new_number}"
done

# Show the created files in a long listing
echo "Created the following files:"
ls -lh ${name}*


