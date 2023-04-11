# Bandit

## James Nagy

### Level 0 -> Level 1

Use the commands `ls` then `cat readme` to find the password.

The password is: `NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL`



### Level 1 -> Level 2

Used the commands `ls -lah` to find the file named "-". Then used `cat ./-" to view the file contents which contained the password.

The password is `rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi`



### Level 2 -> Level 3

I used the command `cat` followed by `sp` then hit tab to complete the filename and view the contents.

The password is `aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG`



### Level 3 -> Level 4

I used the command `ls` to find the directory `inhere`. Then I used `ls` which displayed nothing. So I tried `ls -lah` which showed a hidden file named `.hidden`. I used `cat .hidden` to view the contents.

The password is `2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe`


### Level 4 -> Level 5

I used the command `cd inhere` to change directories. Then I used `ls` to view the files. To find the only human readable file, I used trial & error to find the correct file by using `cat ./-file00` up to `cat ./-file07`. I found the password in the file named `-file07`.

Doing some research on the `file` command, I found a better way to find the human readable file faster. Using the command `file ./-file(asterisk-here)` I was able to find that `-file07` was the only file that contained ASCII text. 

The password is `lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR`



### Level 5 -> Level 6

Using the command `find ./ -type f -size 1033c ! -executable` I was given the output: `./maybehere07/.file2`. Going into this directory and using `cat .file2` I was able to find the password. The `-type f` test specifies a regular file, `-size 1033c` specifies the file only uses 1033 bytes of data, and `! -executable` specifies that the file isn't an executable. 

The password is `P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU`



### Level 6 -> Level 7

Using the command `find . -size 33c -user bandit7 -group bandit6 | grep bandit7` I got a ton of output with directories saying "Permission Denied". But one of the outputs is highlighted, a directory: `./var/lib/dpkg/info/bandit7.password`. I `cd` there and `cat` the file to retrieve the password. 

Running the command `find . -size 33c -user bandit7 -group bandit6 | grep bandit7` in the root directory, I was able to find the password. The `-size 33c` test looks for files 33 bytes in size. The `-user bandit -group bandit6` looks for files owned by the user bandit7 and the group bandit6. The piped command `grep` searched for text strings matching bandit7. 

The password is `z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S`



### Level 7 -> Level 8

Using the command `grep -n 'millionth' data.txt` I found the password to the next level. Using grep, I used the flag `-n` to find the line number and output the ful line name where the string "millionth" is loacted. Running he command, I received the output: `21770:millionth TESKZC0XvTetK0S9xNwm25STk5iWrBvP`. This shows that the string "millionth" is located on line 21770 along with the password string.

The password is `TESKZC0XvTetK0S9xNwm25STk5iWrBvP`



### Level 8 -> Level 9

Using the command `sort data.txt | uniq -u` I was able to find the password. The `sort` command lists the contents in alpha-numerical order, then the `uniq` command filters the output to only show unique lines. That is, the lines that are not repeated. 

The password is `EN632PlfYiZbn3PhVK3XOGSlNInNE00t`



### Level 9 -> Level 10


I just used the previous command from level 8 to find this password. It's easy to spot the equal signs from the output.

The password is `G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s`



### Level 10 -> Level 11

Using the command `base64 -d data.txt` I was able to decode the file and find the password. The `-d` flag used with the `base64` command decodes the file.

The password is `6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM`



### Level 11 -> Level 12

Using the command `cat data.txt | tr '[A-Za-z]' '[N-ZA-Mn-za-m]'` I found the password to the next level. Using the `tr` command, we can use two sets as input and use the input from our file to decode it using rot13 (rotated by 13 positions). If you `cat` the file before decoding, it's `Gur cnffjbeq vf WIAOOSFzMjXXBC0KoSKBbJ8puQm5lIEi`. And after you rotate each letter by 13 positions, you get the following output:

The password is `JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv`



### Level 12 -> Level 13

Not gonna lie, I got very stuck on this level. I had to do lots of googling and eventually caved in and found a solution. This level involves checking the file type with `file`, modifying the suffix of the filewith `mv`, and decompressing the file with `gzip`, `bzip2`, or `tar`. Doing these steps about 9 times eventually gives you a file type of ASCII. Using `cat` on this file gives the password.

The password is `wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw`



### Level 13 -> Level 14

For this level, we need to `ssh` into bandit14 using the provided private key. Using `nmap -p 1-65535 localhost.` we can find a list of open ports to use. I used port 2220 to `ssh` into. Using the command `ssh -i sshkey.private bandit14@localhost -p 2220` I was able to successfully `ssh` into bandit14. Using `cat /etc/bandit_pass/bandit14` I was able to find the password. 

The password is `fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq`



### Level 14 -> Level 15

Using the command `telnet localhost 30000` we can connect to localhost on port 30000. Providing the previous password, we get the password to the next level. 

The password is `jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt`



### Level 15 -> Level 16

Using the command `openssl s_client -quiet -connect localhost:30001` I was able to use `openssl` to retrieve the password. `-quiet` prevents the the session and certificate info from printing. `-connect` tests the connection to the service. `localhost:30001` is the IP and Port we want to connect to.

The password is `JQttfApK4SeyHwDlI9SXGR50qclOAil1`



### Level 16 -> Level 17

To find the ports we can connect to, we run the command `nmap -p 31000-32000 localhost.`. This gives us five ports we can connect to using the command `openssl s_client -quiet -connect localhost:PORT_NUM`. After some trial and error, Port 31790 speaks SSL and gives us the private key when we give the password to the current level. We then use this private key to SSH into the next level.

The password is a private key:
```
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----
```



### Level 17 -> Level 18

Finding the password to the next level is pretty simple. Just run the command `diff passwords.new passwords.old` and you get the output:

```
42c42
< hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg
---
> f9wS9ZUDvZoo3PooHgYuuWdawDFvGld2
```
The first string being the password.

The password is `hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg`



### Level 18 -> Level 19

Using the command `ssh -p 2220 bandit18@bandit.labs.overthewire.org cat readme` we can `ssh` into level 18. Once we provide the level's password, the `cat readme` command gets us the password before we get logged out.

The password is `awhqfNnAbc1naukrpqDYcF95h7HoMTrC`



### Level 19 -> Level 20

To find the password for the next level, we need to run the file `bandit20-do` along with the command we want to run as bandit20. Using this file, we run the command `./bandit20-do cat /etc/bandit_pass/bandit20` and we get the password. 

The password is `VxCazJaVykI6W36BkBU0mJTCM8rR95XT`



### Level 20 -> Level 21

I got stuck on this level as well, and had to look up help online. I found that if you run this command `echo "GbKksEFF4yrVs6il55v6gwY5aVje5f0j" | nc -l localhost -p 61337 &` in the background using `&` you can set up a listener for the binary file to connect to on the same port. Now we run the command `./suconnect 1234` and get the following output: 

```
Read: VxCazJaVykI6W36BkBU0mJTCM8rR95XT
Password matches, sending next password
NvEJF7oVjkddltPSrdKEFOllh9V1IBcq
[1]+  Done                    echo "VxCazJaVykI6W36BkBU0mJTCM8rR95XT" | netcat -lp 1234
```

The password is `NvEJF7oVjkddltPSrdKEFOllh9V1IBcq`
