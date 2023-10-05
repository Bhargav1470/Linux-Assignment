# Linux-Assignment

#Question 1 : Configure smtp in localhost.<br>
Ans :
1. Install postfix. <br>
        ***sudo apt install postfix***
2. A window will open for postfix configuration ,select internet site, press tab >>enter <br>
     then u can give system mail name for ex : host.example.com
3. After configuration, make changes in main.cf file present in /etc/postfix/main.cf <br>
         ***sudo nano /etc/postfix/main.cf***  <br>
   editor will open, scroll down make change in ***inet_interfaces*** from ***all*** to ***loopback-only***. <br>
4. Install mailutils. <br>
         ***sudo apt install mailutils*** <br>
5. Send a mail. <br>
         ***echo 'enter body' | mail -s 'enter subject' receiver@gamil.com***

#Question 2 : Create a user in your localhost, which should not be able to execute the sudo command. <br>
Ans: 
1. To create user (to create in bash) <br>
         ***sudo useradd -g groupname -s /bin/bash -c "description" -m -d /home/username username*** <br>
       to create in default shell <br>
         ***sudo useradd username*** <br>
2. To add password. <br>
         ***sudo passwd username***  <br>
3. By default newly created user will not have sudo permissions

#Question 3 : Configure your system in such a way that when a user type and executes a describe command from anywhere of the system it must list all the files and folders of the user's current directory. <br>
Ans:
1. Create a file name describe. <br>
          ***sudo nano /usr/local/bin/describe*** <br>

2. Add script in describe. <br>
          ***sudo nano describe*** <br>
          add <br>
          ***#!/bin/bash <br>
              ls -a***
   

         
    
     

         


     
