# Development Notes
Author : shaon majumder

<h1>DevOps</h1>
<br>
<br>

----------------
## Online Tools
----------------
- JSON Formater
https://jsonformatter.curiousconcept.com/
<br>
<br>

----------------
## Bash Commands and Error Fix For Developers and Devops
----------------
- git without sudo to current user
  ```bash
  sudo chown -R $USER:$USER .
  ```
- for hidden folders like .git
  ```bash
  sudo chown -hR $USER:$USER .
  ```
<br>

----------------

## API Must Know
### HTTP Methods

| HTTP Verb | CRUD | Entire Collection (e.g. /customers) | Specific Item (e.g. /customers/{id}) |
| ------- | ---- | ------------------------------------- | ------------------------------------ |
| POST | Create | 201 (Created), 'Location' header with link to /customers/{id} containing new ID. | 404 (Not Found), 409 (Conflict) if resource already exists.. |
| GET | Read | 200 (OK), list of customers. Use pagination, sorting and filtering to navigate big lists. | 200 (OK), single customer. 404 (Not Found), if ID not found or invalid. |
| PUT | Update/Replace | 405 (Method Not Allowed), unless you want to update/replace every resource in the entire collection. | 200 (OK) or 204 (No Content). 404 (Not Found), if ID not found or invalid. |
| PATCH | Update/Modify | 405 (Method Not Allowed), unless you want to modify the collection itself. | 200 (OK) or 204 (No Content). 404 (Not Found), if ID not found or invalid. |
| DELETE | Delete | 405 (Method Not Allowed), unless you want to delete the whole collection—not often desirable. | 200 (OK). 404 (Not Found), if ID not found or invalid. |

Links
- https://www.restapitutorial.com/lessons/httpmethods.html#:~:text=The%20primary%20or%20most%2Dcommonly,but%20are%20utilized%20less%20frequently.

## Markdown Cheetsheet
----------------
- https://wordpress.com/support/markdown-quick-reference/
- https://www.markdownguide.org/basic-syntax/
- https://www.markdownguide.org/extended-syntax/
- create space between paragraph markdown - https://stackoverflow.com/questions/20543454/create-two-blank-lines-in-markdown
<br>
<br>

----------------
## Git Commands
----------------
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
<br>

----------------
## Elastic Search
----------------
Elastic Search integration in laravel application - https://www.youtube.com/watch?v=aCpsSIY_2eU
Logstash - https://www.elastic.co/logstash/#:~:text=Logstash%20is%20a%20free%20and,to%20your%20favorite%20%22stash.%22

----------------
## Jenkins Setup
----------------
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

<br>
<br>

---------------
## Slate Notes
---------------
### Install Slate Natively - Ubuntu
```bash
sudo apt install ruby ruby-dev build-essential libffi-dev zlib1g-dev liblzma-dev nodejs patch
```
install bundler
```bash
sudo gem update --system
sudo gem install bundler
```

**Note**

If you get the following error<br>
ERROR: Your RubyGems was installed trough APT, and upgrading it through RubyGems itself is unsupported. <br>
try the following commands instead:
```bash
sudo apt-get update -y
sudo apt-get install -y bundler
```

Downloading
```bash
git clone https://github.com/slatedocs/slate.git
cd slate
```
Building gem packages
```bash
bundle install
cd source
bundle exec middleman build
```

Thor errors
```bash
sudo dpkg -r --force-depends ruby-thor
sudo gem install thor
```

You have already activated thor 1.2.1, but your Gemfile requires thor 1.1.0. Prepending `bundle exec` to your command may solve this.
```bash
sudo bundle clean --force
```

Further Tutorial For Slate - https://qomarullah.medium.com/create-api-docs-using-slate-3b90565333d0

Reading
- https://github.com/slatedocs/slate
- https://github.com/slatedocs/slate/wiki/Using-Slate-Natively
- https://stackoverflow.com/questions/70364903/superclass-mismatch-for-class-command
- https://stackoverflow.com/questions/6317980/you-have-already-activated-x-but-your-gemfile-requires-y

<br>
<br>

-----------
## Kubernetes
-----------
- What is kubernetes - https://www.youtube.com/watch?v=cC46cg5FFAM<br>
- How to run containers on Kubernetes - kubernetes(hanlde cluster of containers) -> docker(container) https://www.youtube.com/watch?v=_2fiMli8p3E<br>
- pod - collection of multiple containers<br>
- read later
  - https://www.youtube.com/watch?v=VQUZF6k6g88<br>
  - https://www.youtube.com/watch?v=s_o8dwzRlu4<br>
<br>
<br>

-----------
## Docker
-----------
Reading
- https://docs.docker.com/engine/install/ubuntu/

Installing and hello world Docker
```bash
sudo apt-get remove docker docker-engine docker.io containerd runc
sudo apt-get update
sudo apt-get install     ca-certificates     curl     gnupg     lsb-release
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo   "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
sudo service docker start
sudo docker run hello-world
```

have to read 
- https://docs.docker.com/get-started/

<br>
<br>

# Senior Software Engineer Stuffs
<br>

<br>
<br>
<br>

## Clean Code
-----------
- Smell Code - https://refactoring.guru/refactoring/smells
<br>
<br>

-----------
## Design Principles
-----------
- Open-Closed Principle - https://blog.mayallo.com/open-closed-principle-the-hard-parts
- Dependency Injection
- loose coupling and tight coupling with laravel
<br>
<br>


----------------
## React Notes
----------------
- ### React Basic Projects 
  - React CV Inspiration
    * https://github.com/tasmidur/react-resume
    * https://tasmidur.netlify.app/
    * https://react-resume-rho.vercel.app/
- ### Changing Header For A Single Request
  - HTTP Interceptors - 
  https://rapidapi.com/guides/http-interceptors-axios
  - append default headers of axios for single request
  https://rapidapi.com/guides/request-headers-axios
  - Using Axios to set request headers
  https://blog.logrocket.com/using-axios-set-request-headers/
- React Global State - Small State Management For authentication and other purposes
https://aaronshivers.com/global-state-in-react
- Protected Routes
https://www.makeuseof.com/create-protected-route-in-react/

- ### Redux State Mangement Notes
  We use redux when we have to manage state for lage data for crud or other applications
  - https://redux.js.org/tutorials/essentials/part-1-overview-concepts
  - https://redux.js.org/introduction/getting-started
  - https://redux-toolkit.js.org/usage/usage-guide
  - https://github.com/SajalAhmed/Mini-Twitter

<br>
<br>

----------------
## Laravel Notes
----------------
-Translation 
  - https://github.com/barryvdh/laravel-translation-manager#readme
  - https://github.com/Laravel-Lang/lang
  - https://laravel-lang.com/
  - https://dev.to/jeromew90/how-to-create-a-multilingual-project-in-laravel-internationalization-i18n-11ol
- API Structure
- Sanctum
https://laravel.com/docs/8.x/sanctum
- Sanctum SPA
https://laravel.com/docs/8.x/sanctum#spa-authentication
- Send Bearer Token with Axios
  * https://www.folkstalk.com/2022/09/axios-send-bearer-token-with-code-examples.html
  * https://stackoverflow.com/questions/40988238/sending-the-bearer-token-with-axios
<br>
<br>

-----------
## Mysql Notes
-----------
- Import Database from Console
mysql -u user -p database_name < 'sql_file_path'
<br>
<br>

-----------
## Backend Mechanisms
-----------
How SQL works under the hood - https://blog.bytebytego.com/p/ep20-how-sql-works-under-the-hood?utm_campaign=post&utm_medium=web
<br>
<br>

-----------
## Microservice
-----------
- API GATEWAY -> LAMBDA -> Microservices
- Another Gateway - WSO2
- SSO - Single Sign on
<br>
<br>
