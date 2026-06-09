# DOCUMENTATION

## Task 1
#### 1. `for_loop.sh`
```
#!/bin/bash

fruits=("Apple" "Banana" "Mango" "Orange" "Grapes")

for fruit in "${fruits[@]}"; do
    echo "Fruit: $fruit"
done
```
*Output:*
```Fruit: Apple
Fruit: Banana
Fruit: Mango
Fruit: Orange
Fruit: Grapes
```

#### 2. `count.sh`
```
#!/bin/bash

# Loop from 1 to 10
for i in {1..10}; do
    echo "Number: $i"
done
```
*Output:*
```
Number: 1
Number: 2
Number: 3
Number: 4
Number: 5
Number: 6
Number: 7
Number: 8
Number: 9
Number: 10
```

## Task 2
#### `countdown.sh`
```
#!/bin/bash

# Ask for a number
read -p "Enter a number to start countdown: " num


while [ $num -ge 0 ]; do
    echo "$num"
    num=$((num - 1))
done

echo "Done!"
```

## Task 3
#### 1. `greet.sh`
```
#!/bin/bash

# Check if argument is provided
if [ $# -eq 0 ]; then
    echo "Usage: ./greet.sh <name>"
    exit 1
fi

# $1 is the first argument
name=$1
echo "Hello, $name!"
```
*Output:* ubuntu@ip-10-0-0-9:~$ ./greet.sh maria
`Hello, maria!`

#### 2.`args_demo.sh`
```
#!/bin/bash

# Print total number of arguments
echo "Total arguments: $#"

# Print all arguments
echo "All arguments: $@"

# Print script name
echo "Script name: $0"
```

*Output:*
```
Total arguments: 8
All arguments: I am a DevOps with 8 skills 🤗
Script name: ./args_demo.sh.sh
```

## Task 4
#### `Install_pkg.sh`
```
#!/bin/bash

# List of packages to check/install
packages=("nginx" "curl" "wget")

# Loop through packages
for pkg in "${packages[@]}"; do
    echo "Checking $pkg..."

    if dpkg -s "$pkg" &> /dev/null; then
        echo "✅ $pkg is already installed."
    else
        echo "👎 Installing $pkg..."
        apt-get install -y "$pkg"

        # Verify installation
        if dpkg -s "$pkg" &> /dev/null; then
            echo "✅ $pkg installed successfully."
        else
            echo "❌ Failed to install $pkg."
        fi
    fi
    echo "-----------------------------"
done
```
*Output:*
```
Checking nginx...
👎 Installing nginx...
E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?
❌ Failed to install nginx.
-----------------------------
Checking curl...
✅ curl is already installed.
-----------------------------
Checking wget...
✅ wget is already installed.
-----------------------------
```
*Installing failed becoz, I am not a root user*

## Task 5
#### 1.`safe_script.sh` :
```
#!/bin/bash
set -e   #  command fails = exit

# create directory
mkdir /tmp/devops-test || echo "Directory already exists"

# navigate into it
cd /tmp/devops-test || echo "Failed to enter directory"

#  create a file
touch testfile.txt || echo "Failed to create file"

echo " ✔ Script completed successfully."
```
 *Running fine.*

 #### 2. `new_install_packages.sh`
 ```
 #!/bin/bash

# Exit -- if not root
if [ "$EUID" -ne 0 ]; then
    echo "❌ Please run this script as root (use sudo)."
    return 2>/dev/null || exit 1
fi

# List of packages to check/install
packages=("nginx" "curl" "wget")

# Loop through packages
for pkg in "${packages[@]}"; do
    echo "Checking $pkg..."

    if dpkg -s "$pkg" &> /dev/null; then
        echo "✅ $pkg is already installed."
    else
        echo "👎 Installing $pkg..."
        sudo apt-get install -y "$pkg"

        # Verify installation
        if dpkg -s "$pkg" &> /dev/null; then
            echo "✅ $pkg installed successfully."
        else
            echo "❌ Failed to install $pkg."
        fi
    fi
    echo "-----------------------------"
done
```

### What I Learned 
- I focused on leveling up my shell scripting skills by exploring loops,
 command-line arguments, and error handling.
- I learned how to effectively use for and while loops to automate repetitive tasks 
  and how to pass information into scripts using arguments like $1, $2, $#, and $@,$0
- Additionally, I practiced writing a script to automate package installation and implemented
basic error handling to ensure the script responds correctly when tasks fail or require root permissions.
- *I learned `exit vs return` error handling*



