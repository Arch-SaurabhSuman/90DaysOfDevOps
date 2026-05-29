## TASK 
 - Creating a file :- `touch IOops.txt`
 - Writing a file needs **Redirection** (`> and >>`) and echo
 - Reading a file :- `cat`; `tee` ; `head tail less more`
 - removing a file :- `rm` and `rm -rf <file name>

 ---

 ## COMMANDS

 ### create and view

 ```
echo "hello Saab ji" > naukar.txt
echo "Yaha Kalicharan ka bhoot rahta hai Saab ji" >> naukar.txt
echo "Woh din mein jagta hai" >> naukar.txt
echo "Aur raat mein sota hai 😂 " | tee -a naukar.txt
cat naukar.txt

```
### viewing by lines
```

echo "__ HEAD__" &&  head -2 naukar.txt && echo ""
echo "___TAIL__" &&  tail -2 naukar.txt && echo ""

```
### Removing
```

rm naukar.txt || rm -f naukar.txt

```

##### Documentation CMD
- `touch` (create an empty file)
- `cat`   (read full file)
- `head` and `tail` (read parts of a file)
- `tee` (write and display at the same time)


  
