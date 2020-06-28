# Linux Kernel Assignment:
## Problem #1     
## Block System call: 
#### (a) block system call for date command 
```
[chinmayjain@localhost ~]$ date
Sun 28 Jun 2020 10:17:43 AM IST
[chinmayjain@localhost ~]$ sudo chmod -x /bin/date 
[sudo] password for chinmayjain: 
[chinmayjain@localhost ~]$ date
bash: /usr/bin/date: Permission denied
```
#### (b) block system call for Firefox as well
```
[chinmayjain@localhost ~]$ firefox #This starts a new firefox window
[chinmayjain@localhost ~]$ sudo chmod -x /usr/bin/firefox
[chinmayjain@localhost ~]$ firefox
bash: /usr/bin/firefox: Permission denied
```
## Problem #2  
## Play with Directory:
#### (a) create a directory without name from command line
```
[chinmayjain@localhost ~]$ mkdir ' '
[chinmayjain@localhost ~]$ ls
' '        Documents   Music      Public      Videos
 Desktop   Downloads   Pictures   Templates
```
#### (b) create a directory with name "-okgoogle"
```
[chinmayjain@localhost ~]$ mkdir ./-okgoogle
[chinmayjain@localhost ~]$ ls
Desktop    Downloads  -okgoogle  Public     Videos
Documents  Music      Pictures   Templates
```
Or
```
[chinmayjain@localhost ~]$ mkdir -- -okgoogle
[chinmayjain@localhost ~]$ ls
Desktop    Downloads  -okgoogle  Public     Videos
Documents  Music      Pictures   Templates
```
Source: https://www.tecmint.com/manage-linux-filenames-with-special-characters/
