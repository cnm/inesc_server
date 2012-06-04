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
