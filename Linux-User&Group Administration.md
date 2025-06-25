## 1.Create users and group
1. Command for creating a group called “engineers”: 

       groupadd engineers
2. Creating “devuser1”:  

       mkdir /home/devuser1

       useradd -m -s /bin/bash -b /home/devuser1 -d /home/devuser1 devuser1

       cp /etc/skel/.* /home/devuser1

        chown -R devuser1:devuser1 /home/devuser1
3.	To set a comment "Developer One"

        usermod -c “Developer One” devuser1
4.	creating “devuser2”

        adduser devuser2
5.	change the home directory to custome home directory /customhome/devuser2

        mkdir /customhome
  	    mkdir /customhome/devuser2
  	    usermod -d /customhome/devuser2 devuser2
7.	Add users into group “engineers”

  	    usermod -aG engineers devuser1
  	    usermod -aG engineers devuser2
  	
## 2. Set Passwords and Apply Password Policies

1.	Set password for two users

        passwd devuser1
        passwd devuser2
2.	Minimum days between password changes: 2

        chage -m 2 devuser1
3.	Maximum days between password changes: 45

        chage -M 45 devuser1
4.	Warning days before expiration: 7

        chage -W 7 devuser1

## 3. Sudo Access

1.	To add in sudo group

		usermod -aG sudo devuser1

2.	To Verify the User is in the sudo Group
  

  	      groups devuser1

## 4. Account Expiry and Lock

1.	Set an account expiry date for devuser2 (15 days from today).

          chage -E 2025-07-05 devuser2

2.  Lock the devuser2 account temporarily

          usermod -L devuser1

## 5. Verification
1.	Group membership

        groups devuser1

  	    groups devuser2
  	
3.	Password aging policies

        chage -l devuser1

4.	Sudo access

        groups devuser1
  	
6.	Account expiration

        chage -l devuser1

## 6. Clean-Up

1. Delete a user along with their home directory, delete the group

        deluser --remove-home devuser1

        deluser --remove-home devuser2

        groupdel engineers
## 7. Output of the following: 
•	cat /etc/passwd | grep devuser

•	groups devuser1

•	chage -l devuser1

•	sudo -l -U devuser1

•	ls -ld /customhome/devuser2

![image](https://github.com/user-attachments/assets/fd3838f3-d1dd-47da-bae6-eeb291891323)






