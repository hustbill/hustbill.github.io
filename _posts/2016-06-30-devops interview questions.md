---
layout: post
title:  "Shell questions for Devops engineer"
date:   2016-06-30 19:04:08
categories: devops
---

Dima gave me a shell question on this afternoon, here is the solution.  

```code
$ sudo cat *.txt > /bin/a.out
bash: /bin/a.out: Permission denied

```
** Root Cause **  
This command does not work because the redirection is performed by shell which does not have the permission to write to /bin/a.out. The redirection of the output is not performed by sudo.  

** Solution  **  

```code 
There are two solutions to Dima’ shell question:

1. Run a shell with sudo and give the command to it by using the -c option:
$ sudo sh -c 'echo *.txt > /bin/test.out'
$ cat /bin/test.out
*.txt a.txt b.txt

2.Create a script with the commands and run that script with sudo:
#!/bin/sh
echo *.txt > /bin/test2.out

Then, 
$ chmod a+x runRedirect.sh
$ sudo ./runRedirect

$ cat /bin/test2.out
*.txt a.txt b.txt
```

I truly enjoyed learning more about devops role and RealtyShares . After our conversation, I am confident that my skills and experiences are a good match for this opportunity.  

If you need any further information, please do not hesitate to contact me by email or phone. Thanks again, and I hope to hear from you in the near future. 
