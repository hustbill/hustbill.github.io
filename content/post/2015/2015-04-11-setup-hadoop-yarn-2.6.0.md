---
layout:	post
title:	"Hadoop YARN Setting"
date:	2015-04-11 11:49:00
categories: [个人笔记]
---
## Hadoop YARN ##  
1. vi .bash_profile  
add two lines  
<pre> <code> 
export JAVA_HOME=`/usr/libexec/java_home -v 1.7`
export HADOOP_PREFIX=/usr/local/Cellar/hadoop/2.6.0/libexec
</code></pre>

2.SSH
<pre><code>
If you cannot ssh to localhost without a passphrase, execute the following commands:

$ ssh-keygen -t dsa -P '' -f ~/.ssh/id_dsa
$ cat ~/.ssh/id_dsa.pub >> ~/.ssh/authorized_keys
</code></pre>

3. modify 
<pre><code> 
In the distribution, edit the file etc/hadoop/hadoop-env.sh to define some parameters as follows:

# set to the root of your Java installation
export JAVA_HOME={your java home directory}
# set to the root of your Hadoop installation
export HADOOP_PREFIX={your hadoop distribution directory}
e.g.  /usr/local/Cellar/hadoop/2.6.0/libexec
</code></pre>

