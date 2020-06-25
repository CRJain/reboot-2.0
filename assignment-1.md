# Linux Kernel Assignment:
## Problem #1     
### Block System call: 
#### (a) block system call for date command 
#### (b) block system call for Firefox as well

## Problem #2  
### Play with Directory:
#### (a) create a directory without name from command line
#### (b) create a directory with name "-okgoogle"
```
crjain@linux:~$ mkdir ./-okgoogle
crjain@linux:~$ ls
 Android     Downloads   Pictures   script.txt   typescript
 Desktop     Music       progress   snap         Videos
 Documents   -okgoogle   Public     Templates   'VirtualBox VMs'
```
Or
```
crjain@linux:~$ mkdir -- -okgoogle
crjain@linux:~$ ls
 Android     Downloads   Pictures   script.txt   typescript
 Desktop     Music       progress   snap         Videos
 Documents   -okgoogle   Public     Templates   'VirtualBox VMs'
```
Source: https://www.tecmint.com/manage-linux-filenames-with-special-characters/
