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

