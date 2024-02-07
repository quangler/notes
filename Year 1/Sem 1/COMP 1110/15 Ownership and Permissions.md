to view ownership of a file

  

'ls -l'

- this will give you info on the user owner and the group owner

  

ownership of directory file:

'ls -ld'

- will still show user owner and group owner

  

'stat' also works

  

every object is owned by a user and a group

- the creator is the default owner

  

'chown' - can change the ownership of a file (can only be done by root user)

- ownership is by UID not username

  

the group owner of a file is the creator's primary group.

  

'chgrp' - use it to change group owner to another group the user is in

root can use this any time

uses GID of group, not group name

  

If a user is deleted or UID changed, the old UID is still the owner of the file

if a group is deleted or GID is changed, the old GID is still the group owner of that group's files

  

'newgrp' - changes your effective primary group temporarily

'exit' - quits you out of new group mode

use this to create objects for other groups

  

'chgrp' - change group that owns user's files to a group they belong to

root can use chgrp to any group or GID

'chgrp -R' - recursive, acts upon their subdirectories and contents

  

'chown' - used by root to change user owner, group owner, or both

users can use this to change group owner of their files (use chgrp)

  

**Permissions**

'ls -l' - shows ten characters at start of line (permissions)

  

2-4 are permissions for user owner

5-7 are permissions for group owner

8-10 are permissions for 'other' or world permissions (all users who are not the file owner or a member of the file's group)

  

use rwx and - (read, write, execute and nothing)

  

r - in file means they can view and copy, nothing else

r - in the directory, file names can be listed but nothing else

w - in file means they can write and save (needs r perms too)

w - in the directory, you can add or remove files to directory. (needs x permissions too)

x - in file means they can be executed or run as a process

x - in the directory, user can 'cd' into that directory, and use the directory path names

  

types of files:

'-' | a regular file

d | a directory file

l | symbolic link (points to another file)

  

if you are user that owns file

- first 3 permissions

if you are not the user owner, but a member of the group that owns the file

- second 3 permissions

if you are not the user owner and not a member of the group

- last 3 permissions

  

'chmod' - (change mode) used to set or modify permissions

- need to either be user owner or root
- either in symbolic or numeric method

symbolic

- WHO? > u - user ; g - group ; o - others ; a - everyone
- OPERATOR > + | add ; - | remove ; = | set exactly
- WHAT > r - read ; w - write ; x - execute ; - | nothing

so.. 'chmod u+wx, g=rx, o-r' - for user owner add write and execute, group user exactly read and execute, others remove read

  

numerically

- uses binary for each read write and execute
- 4 = read
- 2 = write
- 1 = execute
- any combo (0, 1, 2, 3, 4, 5, 6, 7) - give exactly the number of bits in what you want

so.. 'chmod 777' - all groups get full privs

  

'umask' - the inverse mask of default permissions

so if file was 666 and umask was 222, new value would be 444

- default typical umask = 002
- default root umask = 022

to change umask ~/.bashrc

  

setuid permission is set on certain **utilities** so than an ordinary user can run it like root

for example: a normal user needs to use the passwd command (do not have access to /bin/passwd)

  

instead of rwx > rws

rw- > rwS

  

'chmod u+s file' or 'chmod 4nnn file' (nnn is original permission mode)

removing setuid

'chmod u-s file' or 'chmod 0nnn file'

  

same thing exists with setgid (but for group perms)

  

'chmod g+s file' or 'chmod 2nnn file'

removing setgid

'chmod g-s file' or 'chmod 0nnn file'

  

sticky bit permission:

allows users to have write permissions in a directory, but cannot remove files/dirs not owned by them

rwx > rwt

rw- > rwT - T does not always mean it's setup wrong

- T can work if the user owner or group owner have execute

  

'chmod o+t file' or 'chmod 1nnn file'

remove sticky bit

'chmod o-t file' or 'chmod 0nnn file'