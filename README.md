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
         ***echo 'enter body' | mail -s 'enter subject' receivermailid@gamil.com***

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
   ```
   #!/bin/bash 
   ls -a
   ```
4. Save file and change permission <br>
         ***sudo chmod +x /usr/local/bin/describe*** <br>
         
5. Execute describe command

#Question 4 : Users can put a compressed file at any path of the linux file system. The name of the file will be research and the extension will be of compression type, example for gzip type extension will be .gz.
You have to find the file and check the compression type and uncompress it. <br>
Ans:
1. To find the Research.zip file. <br>
         ***find / -type f -iname "research.*" 2>/dev/null | egrep "\.(zip|gz|tar|bz2|xz)$"*** <br>

2. Based on file extension use the command to unzip <br>
        for zip file <br>
         ***unzip path filename*** <br>

#Question 5 : Configure your system in such a way that any user of your system creates a file then there should not be permission to do any activity in that file. <br>
Ans :
1. Use umask command for specific session. <br>
         ***umask 0777***
2. Apply umask to root. <br>
         ***sudo nano /etc/login.defs***   (or)   ***sudo nano bash.bashrc*** <br>
         scroll down change umask 022 to 0777 <br>
         
#Question 6 : Create a service with the name showtime , after starting the service, every minute it should print the current time in a file in the user home directory. <br>
Ans :
1. Create a file showtime.sh to write shell script <br>
          ***sudo nano showtime.sh*** <br>
          write script <br>
   ```
   #!/bin/bash 
   while true; do
       date >>"/home/sigmoid/showtime.txt" 
       sleep 60 
   done
   ```

 3. Create a service <br>
          ***sudo nano /etc/systemd/system/showtime.service*** <br>
          write script <br>
    ```
    [Unit]
    Description=Showtime Service

    [Service]
    WorkingDirectory=/home/sigmoid/
    ExecStart=/home/sigmoid/showtime.sh
    Restart=always

    [Install]
    WantedBy=multi-user.target
    ```
 4. Give permission to script file <br>
          ***chmod a+x showtime.sh*** <br>

 5. Reload systemd <br>
          ***sudo systemctl daemon-reload*** <br>
        enable showtime sevice <br>
          ***sudo systemctl enable showtime.service*** <br>
        start showtime service <br>
          ***sudo systemctl start showtime.service*** <br>
        to check showtime service <br>
          ***sudo systemctl status showtime.service*** <br>
        to see contents of showtime.txt <br>
          ***cat showtime.txt*** <br>
        to stop sevice<br>
          ***sudo systemctl stop showtime.service*** 


      
          

         
         



 

         
    
     

         


     
