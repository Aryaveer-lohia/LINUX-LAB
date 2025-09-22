## Enhance and customize a script.

#### ORIGNAL SCRIPT
```bash
#!/bin/bash

for i in 1 2 3 4 5
do
  echo "Number: $i"
done
```
---

#### Editing

🌟Modifying the script in such a way 

➡️User provides start, end, and step values as input.

➡️Script validates inputs (e.g., step must be positive)

![alt text](image.png)


```bash
#!/bin/bash

# Prompt for input
read -p "Enter start value: " start
read -p "Enter end value: " end

# Validate inputs: check if they are integers
if ! [[ "$start" =~ ^-?[0-9]+$ && "$end" =~ ^-?[0-9]+$ ]]; then
  echo "Error: Start and end must be integers."
  exit 1
fi

# Determine direction and loop
if (( start <= end )); then
  for i in $(seq "$start" "$end")
  do
    echo "Number: $i"
  done
else
  echo "Error: Start must be less than or equal to end for automatic step of 1."
  exit 1
fi
```

Breakdown:

➡️ ``` read -p``` prompts the user and stores input.

output of the code 
```bash 
Enter start value: 1
Enter end value: 9
Number: 1
Number: 2
Number: 3
Number: 4
Number: 5
Number: 6
Number: 7
Number: 8
Number: 9
```
---

### 🔧 Q1 Difference between $1, $@, and $# in bash?
Ans= 

🧩 $1, $2, $3, ...
- Represents individual arguments.
- $1 is the first argument, $2 is the second, and so on

🧺 $@
- Represents all arguments as separate words.
- Preserves spaces and allows iteration over each argument.

🔢 $#
- Returns the number of arguments passed to the script.

⚠️ Quick Tip:
If you use $* instead of $@, it treats all arguments as one single string, which can mess up loops or quoted inputs. Stick with $@ when iterating.

### 🔧 Q2 What does exit 1 mean in a script?

Ans=

🔍 What It Means:
- exit ends the script immediately.
- The number 1 is the exit status code.
- 0 usually means success.
- Any non-zero value (like 1, 2, 127, etc.) means failure or error.


🧠 Why Use exit 1?
It helps other programs or users know that the script didn’t complete successfully.