# permissions
Manage who can do what on the system.

## users
### create user
Either `useradd` or `adduser`
```sh
$ sudo adduser -m <name>               # create user + home dir
$ sudo adduser admin --ingroup admin   # create admin user in admin group

# now it's time to make the user the owner of the home dir,
# and set the right permissions for all files within.

$ chown <user>:<user> -R ~/<user>      # recursively change owner
$ chmod 700 /home/<user>               # hide dir from other users
$ chsh -s /usr/local/bin/bash <user>   # change login shell
```
or alternatively:
```sh
$ sudo adduser -m <user>  # does all of the above in a single command except
```

## groups
Groups have combined settings; individual users can be added to groups which
then inherit the permissions of the group.

### create group
```sh
$ groupadd <name>
```

### add user to group
```sh
$ sudo usermod -G <group> <user>
$ sudo usermod -a -G docker ec2-user
```

### add hostname to /etc/hosts
Sometime a 'host not found' error pops up. This means that the host is not in
the hostfile. This is a common error on remote servers. In order to add the
ip, create a mapping such as:
```txt
127.0.0.1 localhost  # alias localhost to 127.0.0.1
```

## passwords
### edit password
```sh
# opens interactive session
$ sudo passwd <user>
```

## namespaces
[tbi]

## default dir permissions
```sh
$ chmod 07555
```

## give specific user permissions for dir
```sh
# change owner
$ sudo chmod <username>: <dirname>

# give write permissions
$ sudo chmod u+w <dirname>
```

```sh
# add user to group associated with directory
$ sudo usermod -a -G <groupname> <username>

# give group write permissions
$ sudo chmod g+w <dirname>
```

## Change user
```sh
# possibly prepend with "sudo"
$ su - <username>
$ whoami
# => <username>
```
- http://stackoverflow.com/questions/11919391/postgresql-error-fatal-role-username-does-not-exist
