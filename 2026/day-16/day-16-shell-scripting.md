# DOCUMENTATION

## Task 1
`hello.sh`
```
#!/bin/bash
echo "Hello DevOps!"
```
*Output:*
`Hello DevOps!`

**Notes:** There is no change after I remove `shebang`. coz, my
current $SHELL= bash. `When i write a shell which don't support bash
iteration then may give error or something.`

## Task 2
`variable.sh`
```
#!/bin/bash
NAME="Aryan"
ROLE="DevOps Engineer"
echo "Hello, I am $NAME and I am a $ROLE"
```
*Output:*
Double quotes: `Hello, I am Aryan and I am a DevOps Engineer`

**Notes:** In single quotes , the variable not assign and output the `literal string` at it is
`Hello, I am $NAME and I am a $ROLE`

## Task 3
`greet.sh`

```
#!/bin/bash
read -p "Enter your Name: " NAME
read -p "Enter your Favourite tool [GitHub,Jira or Slack]: " TOOL
echo "Hello $NAME, your favourite tool is $TOOL"
```
*Output:* `Hello Billy, your favourite tool is Slack`

## Task 4
1.  `check_number.sh`
```
#!/bin/bash
read -p "Enter a number: " num

if [ $num -gt 0 ]; then
    echo "The number is positive."
elif [ $num -lt 0 ]; then
    echo "The number is negative."
else
    echo "The number is zero."
fi
```


2. `file_check.sh`
```
#!/bin/bash
read -p "Enter a filename: " filename

#   file [-f ]
if [ -f "$filename" ]; then
    echo "File '$filename' exists."
else
    echo "File '$filename' does not exist."
fi
```

## Task 5
`server_check.sh`
```
#!/bin/bash

# choose a service
echo "Choose a service:"
echo "1) sshd"
echo "2) nginx"
read -p "Enter choice (1 or 2): " choice

# Map choice
if [ "$choice" = "1" ]; then
    SERVICE="sshd"
elif [ "$choice" = "2" ]; then
    SERVICE="nginx"
else
    echo "Invalid choice."
    exit 1
fi

# check status
read -p "Do you want to check the status? (y/n): " check

if [ "$check" = "y" ]; then
    if systemctl is-active --quiet "$SERVICE"; then
        echo "✅ $SERVICE is active."
    else
        echo "❌ $SERVICE is NOT active."
    fi
else
    echo "Skipped."
fi
```

#### What I Learned
- I focused on advanced Shell Scripting for real-world scenarios.
- I practiced writing scripts to automate system health checks,
 such as monitoring disk space and service status.
- I learned how to use conditional statements to check if services like Nginx or SSH are active
 and how to handle user input for dynamic scripting.

 
