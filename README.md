# Development Notes
Author : shaon majumder

## Online Tools
- JSON Formater
https://jsonformatter.curiousconcept.com/

## Bash Commands and Error Fix For Developers and Devops
- git without sudo to current user
    ```bash
    sudo chown -R $USER:$USER .
    ```
## Markdown Cheetsheet
https://wordpress.com/support/markdown-quick-reference/

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

## React Notes
- HTTP Interceptors
https://rapidapi.com/guides/http-interceptors-axios
- append default headers of axios for single request
https://rapidapi.com/guides/request-headers-axios
- Using Axios to set request headers
https://blog.logrocket.com/using-axios-set-request-headers/
- React Global State - Small State Management For authentication and other purposes
https://aaronshivers.com/global-state-in-react
- Protected Routes
https://www.makeuseof.com/create-protected-route-in-react/

### Redux State Mangement Notes
We use redux when we have to manage state for lage data for crud or other applications
- https://redux.js.org/tutorials/essentials/part-1-overview-concepts
- https://redux.js.org/introduction/getting-started
- https://redux-toolkit.js.org/usage/usage-guide
- https://github.com/SajalAhmed/Mini-Twitter

## Laravel Notes
- Sanctum
https://laravel.com/docs/8.x/sanctum
- Sanctum SPA
https://laravel.com/docs/8.x/sanctum#spa-authentication
- Send Bearer Token with Axios
  * https://www.folkstalk.com/2022/09/axios-send-bearer-token-with-code-examples.html
  * https://stackoverflow.com/questions/40988238/sending-the-bearer-token-with-axios
