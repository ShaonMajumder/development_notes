# Development Notes
Author : shaon majumder

## Bash Commands and Error Fix For Developers and Devops
- git without sudo to current user
    ```bash
    sudo chown -R $USER:$USER .
    ```

## Git Commands
```bash
git add .
git commit -m "message"
git push origin master
git branch new_branch_name
git checkout commit/branch
git branch -m new_branch_name
git branch -D branch_name
git branch -m old_name new_name
git config credential.helper store
git config user.email "you@example.com"
git config user.name "Your Name"
```

## Jenkins Setup
https://www.jenkins.io/doc/book/installing/linux/#debianubuntu

Install jdk
```bash
sudo apt install openjdk-11-jdk
```
Check Java Version
```bash
java -version
```
Install git
```bash
sudo apt install git
```
Install Maven
```bash
sudo apt install maven
```
Check Maven Version
```bash
mvn -version
```
Install Jenkins
```bash
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```

Enable Jenkins Service
```bash
sudo systemctl enable jenkins
```

Get Jenkins Dashboard Password
```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword 
```

Setting Dashboard
- get the password and paste to http://localhost:8080/
- Install suggested plugins 
- Create First Admin User

#### Change Jenkins Port 
(use it when it is interfering with any program)

change jenkins file
```bash
code /usr/lib/systemd/system/jenkins.service
```
Change to `Environment="JENKINS_PORT=8085"`
and save

Reload Systems
```bash
systemctl daemon-reload
```
Restart and Check Jenkins status
```
sudo service jenkins restart
sudo systemctl status jenkins
```

If didnt work edit file
`/etc/default/jenkins` 
change `HTTP_PORT=8080`