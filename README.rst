INESC Server Commands
=====================

Words in *italics* represent a variable.

Update the server
-----------------

    sudo apt-get update

    sudo apt-get upgrade

Add a new user
--------------

    sudo adduser *newusername*

When it asks for the user properties::

   In room number insert where the user is normally located
   In Work phone the phone extension of the room.
   In the home phone, his personal mobile.
   In the other property, insert the group the user belongs to and who is responsible for him

Then move the home of the user from the default folder to the group folder

    sudo mv /home/*newusername* /home/*[root|gaips]*/

And change it in /etc/passwd:

    *newusername*:x:1000:1000:Some Name,,,:/home/**[root|gaips]**/*newusername*:/bin/bash

Also, create its imap directory structure (TODO this should be in the skel):

    maildirmake


Remove a user
-------------

    sudo userdel *oldusername*

And to avoid regrets:

    sudo mv /home/*changethis*/*oldusername* /home/to_delete

(optional) Check if everything is ok at /etc/passwd

Reset a user's password
-----------------------

    sudo passwd *username*

::

    Upon UNIX prompt for a new password, enter a new one
    Be sure to confirm by retyping the same new password when prompted again
    Send the new password to the user who requested the password reset

Missing memory (RAM) in the server
----------------------------------

If the memory reported by free is noticeably different from the sum of `ps aux` read the slabtool response in this site:

http://stackoverflow.com/questions/5463800/linux-memory-reporting-discrepancy

It is basically being used in the kernel for caching purposes.

Update backports
----------------

Add to the repo list:

    deb http://backports.debian.org/debian-backports/ squeeze-backports main

Then:

    sudo aptitude -t squeeze-backports install "mosh"

    sudo apt-get -t squeeze-backports install "mosh"

Repairing mysql tables
----------------------

Check if something is broken:

    myisamchk  /var/lib/mysql/some_database/\*.MYI

To repair tables:

    myisamchk -r -q /var/lib/mysql/some_database/\*.MYI

Check raid status
-----------------

    mdadm --detail /dev/md*

Mailman admin
-------------

Managed by:

    newlist and rmlist

Old instructions:

    | comandos newlist e rmlist
    | devido 'a maquina nao ter ip publico e os nomes gaips e tagus serem cname,
    | os emails podem chegar @inesc-0.tagus.ist.utl.pt
    | por isso é necessario acrescentar a nova lista na linha 9 do ficheiro
    | /etc/exim/conf.d/router/970_local_mailman
    | depois recriar a configuracao do exim com dpkg-reconfigure exim4-config (e'
    | automaticamente reiniciado)
    |
    | o ideal seria a maquina ter ip publico e registos mx
    | por enquanto nao sera' possivel ter dominios virtuais de email
    |
    | exim -bt [-d] <endereco de email>
    | permite testar se o exim consegue entregar o email
    
If having problem with other domains then tagus.inesc-id.pt:

* In file vim /etc/mailman/mm_cfg.py
- Line 100

    | POSTFIX_STYLE_VIRTUAL_DOMAINS = [ 'tagus.inesc-id.pt', 'gaips.inesc-id.pt' , 'citysdk.ist.utl.pt']

* Restart exim4
* Possibly do newaliases comand???
* If nothing works, check if DNS MX record is working
    




