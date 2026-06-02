# DOCUMENTATION

## Task `1 to 4`
![file-prem](day10.png)

## Task 5
 1. Writing in read-only : permission denied to `devops.txt`
 2. executing `script.sh` without x permission : Permission denied.
 3. ```
    ubuntu@ip-172-31-26-105:~$ echo "hhhhh" >> devops.txt
    -bash: devops.txt: Permission denied

    ubuntu@ip-172-31-26-105:~$ chmod 666 script.sh
    ubuntu@ip-172-31-26-105:~$ ./script.sh
    -bash: ./script.sh: Permission denied

    ```
### Permission changed
- before
   ```
   ubuntu@ip-172-31-26-105:~$ ls -l devops.txt notes.txt script.sh
   -rw-rw-r-- 1 ubuntu ubuntu  0 Jun  2 15:48 devops.txt
   -rw-rw-r-- 1 ubuntu ubuntu 20 Jun  2 15:48 notes.txt
   -rw-rw-r-- 1 ubuntu ubuntu 33 Jun  2 15:49 script.sh

   ```
- after
  ```
   ubuntu@ip-172-31-26-105:~$ ls -l devops.txt notes.txt script.sh
   -r--r--r-- 1 ubuntu ubuntu  0 Jun  2 15:48 devops.txt
   -rw-r----- 1 ubuntu ubuntu 20 Jun  2 15:48 notes.txt
   -rwxr-xr-x 1 ubuntu ubuntu 33 Jun  2 15:49 script.sh
  ```

### What I learned

1. Learned how to identify and modify file permissions using commands like ls -l and chmod to resolve access issues.
2. Explored how read, write, and execute permissions affect different file types 
3. Practical Troubleshooting: Like , Write on read-only file & without execute prem. running sh files.
