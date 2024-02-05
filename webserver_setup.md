1. Once logged into AWS, "Launch instance" to create an instance

2. Give it a name

3. Select AMI of choice: Ubuntu in my case

4. Create new key pair or use existing one

5. In Network settings, click Allow SSH traffic from Anywhere, Allow HTTPS and HTTP traffic

6. Once finished, click "Launch instance"

7. Go to Command Prompt on Windows and sign into the server via: 
    ssh -i ~/Location/key.pem ubuntu@3.96.193.99 
    where "key.pem" is the key, "3.96.193.99" is the IP address, and "ubuntu" is the chosen AMI

8. Type "yes" to continue connecting if prompted to do so

9. Make sure server packages are up to date via: 
    sudo apt update

10. Install Apache2 via: 
    sudo apt install apache2 -y

11. Create the txt file in the web root directory of Apache via: 
    sudo nano /var/www/html/comp370_hw2.txt

12. Add some text in the file and save it

13. To allow port 8008 traffic through, edit the Apache ports config file via:
    sudo nano /etc/apache2/ports.conf

14. Add "Listen 8008" in the file and save it

15. Restart the Apache server to apply the changes:
    sudo systemctl restart apache2

16. Open your browser and check:
    http://3.96.193.99:8008/comp370_hw2.txt
    


