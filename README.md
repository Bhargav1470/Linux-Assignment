# Linux-Assignment

#Question 1 : Configure smtp in localhost.<br>
Ans :
1. Install postfix. <br>
        ***sudo apt install postfix***
2. A window will open for postfix configuration ,select internet site, press tab >>enter <br>
     then u can give system mail name for ex : host.example.com
3. After configuration, make changes in main.cf file present in /etc/postfix/main.cf <br>
         ***sudo nano /etc/postfix/main.cf***
   editor will open, scroll down make change in ***inet_interfaces*** from ***all*** to ***loopback-only**. <br>
4. 


     
