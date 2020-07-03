# Linux Kernel Assignment:
## Problem #1     
## Block System call: (still looking for answers)
#### (a) block system call for date command 
```
```
#### (b) block system call for Firefox as well
```
```
## Problem #2  
## Play with Directory:
#### (a) create a directory without name from command line
```
[chinmayjain@localhost ~]$ mkdir $'\n'
```
![ls](https://github.com/CRJain/reboot-2.0/blob/master/image.png)
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
Source:
> https://www.tecmint.com/manage-linux-filenames-with-special-characters/
## Problem #3
## Create a Directory Structure:
![Question](https://1.bp.blogspot.com/-x6vLWgVIU7Q/XvjlJyKJsnI/AAAAAAAAU0M/lmH8ddGkm90gXPNwUZCUvwCTN6XfJINZgCLcBGAsYHQ/s320/Screenshot%2B2020-06-29%2Bat%2B12.12.55%2BAM.png)
```
[chinmayjain@localhost ~]$ mkdir -p A/{B/{G/K,H/J},C/{I/J,J/L},D/{E/M,F/L}}/Reboot.txt
[chinmayjain@localhost ~]$ tree A
A
├── B
│   ├── G
│   │   └── K
│   │       └── Reboot.txt
│   └── H
│       └── J
│           └── Reboot.txt
├── C
│   ├── I
│   │   └── J
│   │       └── Reboot.txt
│   └── J
│       └── L
│           └── Reboot.txt
└── D
    ├── E
    │   └── M
    │       └── Reboot.txt
    └── F
        └── L
            └── Reboot.txt

21 directories, 0 files
```
## Problem #4
#### (a) create two users named Jack and Jill from command line
```
[chinmayjain@localhost ~]$ sudo adduser Jack
[chinmayjain@localhost ~]$ sudo passwd Jack 
Changing password for user Jack.
New password: 
BAD PASSWORD: The password is shorter than 8 characters
Retype new password: 
passwd: all authentication tokens updated successfully.
[chinmayjain@localhost ~]$ sudo adduser Jill
[chinmayjain@localhost ~]$ sudo passwd Jill
Changing password for user Jill.
New password: 
BAD PASSWORD: The password is shorter than 8 characters
Retype new password: 
passwd: all authentication tokens updated successfully.
```
#### (b) login with Jack user and create a file name Jack.txt using vim editor and write "Hello Jack"
```
[chinmayjain@localhost ~]$ su - Jack
Password:
[Jack@localhost ~]$ vim Jack.txt
Hello Jack
~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                              
:wq
[Jack@localhost ~]$ cat Jack.txt 
Hello Jack
```
#### (c) from Jack user also create two directories named Jack1 & Jack2
```
[Jack@localhost ~]$ mkdir Jack1 Jack2
[Jack@localhost ~]$ ls
Jack1  Jack2  Jack.txt
```
#### (d) now login from Jill user and create a file Jill.txt using vim editor and write "Hello Jill"
```
[Jack@localhost ~]$ su - Jill
Password: 
[Jill@localhost ~]$ vim Jill.txt
Hello Jill
~                                                                              
~                                                                              
~                                                                              
~                                                                              
~                                                                                                                        :wq
[Jill@localhost ~]$ cat Jill.txt 
Hello Jill
```
#### (e) from Jill user also create two directoires named Jill1 & Jill2
```
[Jill@localhost ~]$ mkdir Jill1 Jill2
[Jill@localhost ~]$ ls
Jill1  Jill2  Jill.txt
```
#### (f) swap these files and directories in between users (don't use root account)
```
[Jill@localhost ~]$ su - Jack 
Password:
[Jack@localhost ~]$ chmod 777 -R /home/Jack/
[Jack@localhost ~]$ ls -l
total 12
drwxrwxrwx. 2 Jack Jack 4096 Jul  3 12:31 Jack1
drwxrwxrwx. 2 Jack Jack 4096 Jul  3 12:31 Jack2
-rwxrwxrwx. 1 Jack Jack   11 Jul  3 12:31 Jack.txt
[Jack@localhost ~]$ su - Jill
Password:
[Jill@localhost ~]$ chmod 777 -R /home/Jill/
[Jill@localhost ~]$ ls -l
total 12
drwxrwxrwx. 2 Jill Jill 4096 Jul  3 12:34 Jill1
drwxrwxrwx. 2 Jill Jill 4096 Jul  3 12:34 Jill2
-rwxrwxrwx. 1 Jill Jill   11 Jul  3 12:53 Jill.txt
[Jill@localhost ~]$ mv /home/Jack/Jack1 /home/Jill/
[Jill@localhost ~]$ mv /home/Jack/Jack2 /home/Jill/
[Jill@localhost ~]$ mv /home/Jack/Jack.txt /home/Jill/
[Jill@localhost ~]$ ls
Jack1  Jack2  Jack.txt  Jill1  Jill2  Jill.txt
[Jill@localhost ~]$ su - Jack 
Password: 
[Jack@localhost ~]$ mv /home/Jill/Jill1 /home/Jack/
[Jack@localhost ~]$ mv /home/Jill/Jill2 /home/Jack/
[Jack@localhost ~]$ mv /home/Jill/Jill.txt /home/Jack/
[Jack@localhost ~]$ ls
Jill1  Jill2  Jill.txt
```
Source:
> https://www.guru99.com/file-permissions.html
## Problem #5
## Play with Files and Directories:
#### (a) create 4 files named abc.txt ok fine g.txt under /tmp directory
```
[chinmayjain@localhost ~]$ touch /tmp/{abc.txt,ok,fine,g.txt}
[chinmayjain@localhost ~]$ ls /tmp/
abc.txt
fine
g.txt
ok
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-chronyd.service-pi1fXe
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-colord.service-TSmSmj
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-dbus-broker.service-E9s2Tf
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-earlyoom.service-6JuKtj
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-fwupd.service-S3XeTg
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-geoclue.service-3ua6ph
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-ModemManager.service-N8j1Ff
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-rtkit-daemon.service-Rn0zwg
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-switcheroo-control.service-kqDmfh
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-systemd-logind.service-mtcQQf
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-upower.service-8rbO1f
tracker-extract-files.1000
```
#### (b) create 3 directories aa aaa aaaa under /tmp directory
```
[chinmayjain@localhost ~]$ mkdir /tmp/{aa,aaa,aaaa}
[chinmayjain@localhost ~]$ ls /tmp/
aa
aaa
aaaa
abc.txt
fine
g.txt
ok
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-chronyd.service-pi1fXe
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-colord.service-TSmSmj
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-dbus-broker.service-E9s2Tf
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-earlyoom.service-6JuKtj
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-fwupd.service-S3XeTg
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-geoclue.service-3ua6ph
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-ModemManager.service-N8j1Ff
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-rtkit-daemon.service-Rn0zwg
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-switcheroo-control.service-kqDmfh
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-systemd-logind.service-mtcQQf
systemd-private-7d2d8b03fedc48c4a0526e1726a83082-upower.service-8rbO1f
tracker-extract-files.1000
```
#### (c) give ls command to list the content of /tmp directory [make sure it will only list the content (file|directory)  having 2 char in their name]
```
[chinmayjain@localhost ~]$ ls --hide='???*' /tmp
aa  ok
```
Sources:
> https://www.cyberciti.biz/faq/how-to-delete-files-containing-character-numberdigit/
> https://www.computerhope.com/unix/uls.htm
## Extra Tasks
#### (a) Write in a Directory:
```
[chinmayjain@localhost ~]$ mkdir temp
[chinmayjain@localhost ~]$ setfattr -n user.msg -v "Hello World" temp/
[chinmayjain@localhost ~]$ getfattr -n user.msg temp
# file: temp
user.msg="Hello World"
```
