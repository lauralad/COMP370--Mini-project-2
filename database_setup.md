1. Make sure packages are up to date
    sudo apt update

2. Install MariaDB:
    sudo apt install mariadb-server

3. Run the security installation script of the database
    sudo mysql_secure_installation

4. Follow the prompts and set a password:
    Enter current password for root: Enter
    Switch to unix_socket_authentication: y
    Change root password: y
    New password: ....
    Re-enter: ....
    Remove anonymous users: y
    Disallow root login remotely: y (for security reasons)
    Remove test database and access to it: y
    Reload privilege tables now: y

5. Allow external access by configuring it to listen on external IP:
    sudo nano /etc/mysql/mariadb.conf.d/50-server.cnf

6. Change bind-address parameter and then save file:
    bind-address = 0.0.0.0
    port = 6002

7. Restart MariaDB:
    sudo service mariadb restart

8. Log into MariaDB as root user and enter password:
    sudo mysql -u root -p

9. Create the database:
    CREATE DATABASE comp370_test;

10. Check datatbase is created (should see in the list):
    SHOW DATABASES;

11. Create a new user and grant permissions:
    CREATE USER 'comp370'@'%' IDENTIFIED BY '$ungl@ss3s';
    GRANT ALL PRIVILEGES ON comp370_test.* TO 'comp370'@'%';
    FLUSH PRIVILEGES;

12. Exit MariaDB:
    exit

13. Add Inbound rule for port 6002 in AWS:
    Click on the instance (mole-ratt)
    Scroll down to Details and click Security
    Go to Inbound rules and click on "launch-wizard-4" in Security groups column
    Click "Inbound rules" > "Edit inbound rules"
    Add "Custom TCP" with port range 6002 and save

14. Test the connection from DBeaver:
    click "Database" option from top menu
    Click "New database connection"
    Set host as the IP of server: 3.96.52.230
    Set port: 6002
    username: comp370
    password: $ungl@ss3s
    Click Finish
    