#### Explanation:

### useradd: This creates a new user. 
### chpasswd: This sets the password for the new user. 
### usermod -aG sudo: This adds the new user to the sudo group, granting administrative privileges.
```bash
#!/bin/bash 
# Define username and password 
USER_NAME="newuser" 
USER_PASSWORD="password123" 
# Create the user 
sudo useradd $USER_NAME 
# Set the password for the new user 
echo "$USER_NAME:$USER_PASSWORD" | sudo chpasswd 
# Add user to sudo group 
sudo usermod -aG sudo $USER_NAME
```