
### Install MongoDB Community Edition on CentOS 7

```
$ sudo vi /etc/yum.repos.d/mongodb-org-4.4.repo
Add the following line
[mongodb-org-4.4]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/$releasever/mongodb-org/4.4/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://www.mongodb.org/static/pgp/server-4.4.asc

$sudo yum update -y

$sudo yum install -y mongodb-org

By default, MongoDB runs using the mongod user account and uses the following default directories:

/var/lib/mongo (the data directory)
/var/log/mongodb (the log directory)
```
### Configure SELinux

```
If SELinux is in enforcing mode, you must customize your SELinux policy for MongoDB by making the following two policy adjustments:

For simplicity you can change the SELinux to permissive mode by editing the file /etc/selinux/config 

$vi /etc/selinux/config
# This file controls the state of SELinux on the system.
# SELINUX= can take one of these three values:
#     enforcing - SELinux security policy is enforced.
#     permissive - SELinux prints warnings instead of enforcing.
#     disabled - No SELinux policy is loaded.
```
   **SELINUX=permissive**
```
# SELINUXTYPE= can take one of three values:
#     targeted - Targeted processes are protected,
#     minimum - Modification of targeted policy. Only selected processes are protected.
#     mls - Multi Level Security protection.
SELINUXTYPE=targeted

after that you can either restart the server or simply excute the command 

$ sudo setenforce 0 to disable the selinux till it is restarted.
```
### Run MongoDB Community Edition

```
$ sudo systemctl enable  mongod --now

Check the status if it is running

$ sudo systemctl status mongod

```


