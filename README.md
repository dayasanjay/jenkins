# Jenkins

- What is Jenkins?<br>
- What is CI/CD  ( Continuous Integration Continuous Delivery )<br>
- Stages in CI/CD<br>
- Creating CI/CD Infrastructure in AWS<br>
- Installing Jenkins in EC2 Machine<br>
- How to run a sample job in Jenkins?<br>
- Install Tomcat on AWS Environment<br>
- Performing continuous download<br>
- Performing continuous build<br>
- How to install Plug-in<br>
- Performing continuous Deployment<br>
- Importance of Context Path<br>
- Performing continuous download<br>
- Performing continuous build<br>
- How to install Plug-in<br>
- Performing continuous Deployment<br>
- Importance of Context Path<br>
- How to call one job from another job<br>
- Copy Artifact Plugin<br>
- Performing all the five Stages in CI-CD<br>
- How to create new user in Jenkins<br>
- Types of Roles – Global Role Item / Project Role<br>
- Role based authorization Strategy Plugin<br>
- Need for Master Slave configuration<br>
- Establish password-less connection between Master and Slave Machine<br>
- Creating new node in Jenkins<br>
- Run the job in node machine<br>
- What is Pipeline Job?<br>
- Advantages of Pipeline Job<br>
- Build pipeline plug-in<br>
- Generating the Groovy code<br>
- Perform CI/CD Stages using groovy code<br>
- What is multibranch Pipeline?<br>
- Triggering the pipeline job automatically<br>
- Email Integration in Jenkins<br>
- Trigger the job periodically<br>
- Wait for the approval from delivery head, before moving it to production<br>


# What is Jenkins?

Jenkins is a self contained, open source automation server which can be used to automate all  tasks related to building , testing and delivery activities. Jenkins can be installed even on standalone be any machine with a java runtime envirowment (JRE) Installed.

Jenkins is a tool for Implmenting CI-CD (Continuous Integration - Continuous Delivery)

Stages in CI-CD: <br>

Stage 1 : Continuous Download<br>
Stage 2: Continuous Build<br>
Stage 3: Continuous Deployment<br>
Stage 4: Continuous Testing<br>
Stage 5: Continuous Delivery<br>


1-4----Continuous Integration<br>
  5----Continuous Delivery<br>
  

# Install Jenkins in AWS Instance

To install Jenkins the first thing we need java file so first we need to install java like we have done in the local instance.<br>

We need to download Java 1.8 or more.<br>

1) Update the apt repository<br>
sudo apt update<br>

2) sudo apt install openjdk-8-jdk -y<br>

3) Check the Java Version<br>
java -version<br>

4) Install Maven & Git<br>
sudo apt-get install -y git  maven<br>

5) Check the Verion of Git & Maven<br>
For Git : git --version<br>
For Maven : mvn --version<br>

6) Download & install Jenkins<br>
Open Jenkins website (https://jenkins.io/download/)<br>

Go to Long Term Support<br>

Select Generic Java Package (.war)<br>

We are selecting generic java package file because jenkins will install on those machine where java is already install. If we have java install in windows machine jenkins will work. Only pre requirement is java needs to be install.

For Windows we just need to click on the file and it will download automatically.

For Linux machine enter command wget and paste the url to download the file.<br>

To get the URL right click on generic java package and click on copy link address.<br>

(wget http://mirrors.jenkins.io/war-stable/latest/jenkins.war)<br>

wget  https://get.jenkins.io/war-stable/2.277.2/jenkins.war<br>

11) Start the Jenkins.war file<br>

java -jar jenkins.war<br>

12) Access Jenkins Home Page<br>

Select DEV Instance & Press Connect.<br>

Copy the Domain Name On 4th point.<br>

Paste the Domain name in the browser and in the end enter :8080 with the default port number.<br>

We can access the jenkins with dev server Public IP.<br>

Copy the public ip of the dev server and paste the ip address in the browser and in the end enter :8080 with the default port number.<br>


13) Unclock Jenkins<br>

When we are installing jenkins it will automatically give you the password in the github terminal.<br>

Copy the password and paste the browser.<br>

You will get the password on the step 11<br>

14) Press Install Suggested Plugins<br>

15) Create First admin user<br>

The first user which we create here is the admin user of the jenkins.<br>

Click on save and continue.<br>

Click on save and finish<br>

# Create Sample Job


Build tab<br>
Click on execute Shell<br>
In Command Box Enter echo " Hello Jenkins"<br>
Click on Console Output<br>











--------------------------------------------------------------------------------

# Install TOMCAT In QA & Production Server

1) Select QA Server and connect<br>

2) Copy the SSH Command<br>

3) Open GIT Bash & paste the SSH Command<br>

Press Yes<br>

4) Update the apt repository <br>
sudo apt-get update<br>

5) Install tomcat8<br>
sudo apt-get install -y tomcat8<br>

After this we need to install one more package<br>
sudo apt-get install -y tomcat8-admin<br>

6) Check the tomcat is intall or not<br>

Copy the public IP of the QA Server then paste in the browser and in the end enter :8080 <br>

qa_server_public_ip:8080<br>

Setting the path of tomcat in jenkins<br>

7) enter linux command in QA Server  -   cd /etc/tomcat8/<br>

8) enter linux command in QA Server  -   ls<br>

9) You will find the file tomcat-users.xml<br>

10) Open the file -- sudo vim tomcat-users.xml<br>

11) In the end we need to add one statement <br>
<user username="training" password="bahadoor" roles="manager-script,manager-status,manager-gui"/><br>

save and quit <br>

press esc <br>

type :wq <br>

press enter<br>

12) When ever we do any changes done in any service we need to restart the service<br>
sudo service tomcat8 restart<br>

13) After this the same above 12 steps we need to do in the prod server also.<br>

Prod Instance<br>
<user username="learning" password="bahadoor" roles="manager-script,manager-status,manager-gui"/><br>



First Start All the AWS Machines.<br>

Connect Dev Server<br>

Start the Jenkins <br>

java -jar jenkins.war <br>

<b>Stage 1 : Continuous Download START CI-CD</b><br>

1) Create New item as free style project<br>

2) Click on source code managment <br>

3) Select GIT<br>

4) Enter the URL of github reposiditory<br>
https://github.com/sunildevops77/maven.git<br>

5) Click on apply and save<br>

6) Run the Job<br>

7) Check the console output.<br>

8) Connect to the dev server<br>

9) Go to the location where code is downloaded<br>
sudo su -<br>

cd path of the folder<br>

ls<br>

<b>Stage 2 : Continuous Build</b><br>

Convert the java files in to artifact ( .war file)

10) Click on configure of the same job<br>

11) Go to Build Section<br>

12) Click on add build step<br>

13) Click on Invoke top level maven targets<br>

14) Enter the goal as  package<br>

15) click on apply and save<br>

16) Run the Job<br>

17) Click on number & click on console output<br>

18) Copy the path of the war file and check the file in the linux machine<br>
sudo su -<br>

cd path<br>

ls<br>

<b>Stage 3 :Continuous Deployment</b><br> 

Now we need to deploy the war file into the QA Server.<br>

19) For this we need to install "deploy to container" plugin.<br>
 
Go to Dasboard<br>

Click on manage jenkins<br>

Click on manage plugins<br>

Click on avaiable section<br>

Search for plugin ( deploy to container )<br>

Select that plugin and click on install without restart.<br>

20) Click on post build actions of the development job<br>

21) Click on add post build actions<br>

22) Click on deploy war/ear to container<br>

23) Enter the path of the war file (or)<br>
 we can give **/*.war in war/ear files.<br>

24) Context path: qaenv<br>

25) Containers : select tomcat 8<br>

Credentials : Click on add<br>

select jenkins<br>

enter tomcat user name and password<br>

Click on add<br>

Select credentials.<br>

give the private ip of the QA server.<br>

http://private_ip:8080

26) Click on apply and save<br>

27) Run the job<br>

28) To access the home page<br>

public_ip_Qa_server:8080/qaenv<br>



After testing completed we need to clone the testing code form github<br>
https://github.com/sunildevops77/TestingNew.git<br>


Step 1: Connect to Devserver from git bash<br>
Step 2: Start Jenkins    ( java  -jar  jenkins.war )<br>
Step 3: Create new item  ( Name - testing )<br>
	Source code management tab,  Git<br>
Repository URL - https://github.com/sunildevops77/TestingNew.git<br>

Apply -- Save<br>

Step 4: Run the job.<br>
Step 5: Check the path of the files which are downloaded.<br>
	/home/ubuntu/.jenkins/workspace/testing<br>
Step 6: Configure the same job ( testing )<br>
	Build -- Add build Step  -- Execute shell<br>
 	( Command: java -jar  testing.jar )<br>
	Command:   echo " Testing passed"<br>



Now both are independent job.<br>
To call testing job  after development job is completed<br>

Go to first job ( demo ) --  configure <br>
Post build actions -- add post build action -- build other project -<br> 
Projects to build - testing ( name of the job)<br>

-----------------------------------------------------------------------------


Copying artifacts from development job to testing job<br>

The artifacts (war) created by the development job should be passed to the testing job so that the testing job can deploy that into tomcat in the prod environment.<br>


Install Plugins<br>

1) Go to Jenkins dashboard<br>

2) Go to manage jenkins<br>

3) Click on Manage plugins<br>

4) Search for "Copy Artifact"  plugin<br>

5) Install the plugin<br>

<b>Stage 5 : Continous Delivery</b><br>

1) Go to Development job <br>

2) Go to Configure<br>

3) Go to Post build actions tab<br>

4) Click on add post build action<br>

5) Click on Archive the artifacts<br>

6) Enter **/*.war<br>

7) Click on apply and save<br>

8) Go to testing Job<br>

9) Click on configure<br>

10) Go to Build section<br>

11) Click on add build steps<br>

12) Click on copy artifacts from another project<br>

13) Enter Development as project name<br>

14) For Deployment Go to Post build actions section<br>

15) Click on add post build action<br>

16) Click on deploy war/ear to a container<br>

17) Enter **/*.war in war/ear files<br>

18) Context path : prodenv<br>

19) Click on add container <br>

20) Select tomcat 8<br>

21) Select your Credentials<br>

22) Enter private ip:8080 of the prod server<br>

23) Click on Apply and save<br>



----------------------------------------------------------------------

1) enter linux command in Prod Server  -   cd /etc/tomcat8/

2) enter linux command in prod Server  -   ls

3) You will find the file tomcat-users.xml

4) Open the file -- sudo vim tomcat-users.xml

5) In the end we need to add one statement 
<user username="learning" password="sunilsunil" roles="manager-script,manager-status,manager-gui"/>

6)  we need to restart the service
sudo service tomcat8 restart




# Creating users in Jenkins

1) Open the dashboard of jenkins

2) click on manage jenkins

3) click on manage users

4) clcik on create users

5) enter user credentials

# Creating roles and assgning

1) Install "role based authorization strategy" plugin<br>
2) go to dashboard-->manage jenkins <br>
3) click on configure global security<br>
4 check enable security checkbox<br>
5) go to authorization section-->click on role based    strategy  radio button<br>
6) apply-->save<br>
7) go to dashboard of jenkins<br>
8) click on manage jenkins<br>
9) click on manage and assign roles<br>
10) click on mange roles<br>
11) go to global roles and create a role "employee"<br>
12) for this employee in overall give read access in view section give all access<br>
13) go to project roles-->Give the role as developer and patter as Dev.* (ie developer role can access only those jobs whose name start with Dev)<br>
14) similarly create another role as tester and assign    the pattern as "Test.*"<br>
15) give all permisiinons to developrs and tester<br>
16) apply--save<br>
17) click on assign roles<br>
18) go to global roles and add user1 and user2<br> 
19) check user1 nad user2 as employees<br>
20) go to item roles<br>
21) add user1 and user2<br>
22) check user1 as developer and user2 as tester<br>
23) apply-->save<br>

Restart Jenkins<br>

If we login into jenkins as user1 we can access on the development related jobs and user2 can access only the testing related jobs


# Master-Slave configuration


Same version of java should exist.<br>
Master and slave should have password less SSH<br>

<b>Step 1: Create slave machine  , connect to slave</b><br>

1) Update the apt repository<br>
sudo apt-get update<br>


2)  sudo apt install openjdk-8-jdk -y<br>


3) Check the Java Version<br>
java -version<br>


<b>We need to establish password less connection between Dev server and Slave machine</b>

Connect to slave<br>
4) Check you user<br>
$ whoami       (  ubuntu )<br>


5) set password  for  ubuntu  user<br>
syntax: sudo  passwd  <user_name><br>
Ex:        sudo passwd ubuntu<br>
enter password<br>


$  cd /etc/ssh<br>

$ ls   ( we get list of files )   Look for   sshd_config<br>

To edit sshd_config<br>
$ sudo vim sshd_config<br>

Go to insert mode<br>

6) change password authentication to yes<br>

7) Save and quit :wq<br>

8) Restart the service<br>
$ sudo service ssh restart<br>

Lets test the connection<br>


9) Connect to the development server  ( Master )<br>

10) connect to slave server through dev server<br>
ssh ubuntu@private_ip_slave_machine<br>

$ ssh ubuntu@172.31.1.107<br>



exit  ( to come back to master )<br>

--------------------------------------------------------------------------------------


11)  To connect to slave  without password<br>
$ ssh-keygen      ( In master)<br>


12) copy the keys to slave server<br>
ssh-copy-id  ubuntu@private_ip_slave_server<br>
ssh-copy-id  ubuntu@172.31.1.107<br>



13) now we are able to connect to the slave user without password<br>
$  ssh ubuntu@172.31.1.107<br>


Download slave.jar in slave machine<br>


sudo  wget http://172.31.41.7:8080/jnlpJars/slave.jar<br>



Check the file is download or not<br>
1) ls<br>

check the file permissions<br>
2) ls -l<br>

we want    rwxrw-r--<br>

3) Give execute permissions of this file<br>
sudo chmod u+x slave.jar<br>



4) Create an empty folder which will work like workspace for jenkins to use on the slave machine<br>
 mkdir workspace<br>
 cd workspace<br>
 pwd( note the path of the workspace )-- /home/ubuntu/workspace<br>




# Creating nodes in Jenkins


Open the dashboard of jenkins<br>

manage jenkins --- manage nodes<br>

7) Click on new node ----  node name -  Myslave<br>
		       - select permanent agent<br>

Remote root directory   -/home/ubuntu/workspace<br>
Label - Slave_lab<br>


10) Go to Launch method<br>
Select Launch agent via execution of command on the controller<br>

11) In Launch command<br>
ssh ubuntu@private_ip_of_slave java -jar slave.jar<br>
ssh ubuntu@172.31.1.107     java  -jar   slave.jar<br>


13) Click on save<br>


# Configure job to run on slave


14) Select Testing Job<br>

15) Go to Configure  --> General Tab<br>

17) Check Restrict where this project can be run<br>

18) Enter Label Expression ( Slave_lab)<br>

Apply ---> Save  <br>
Run the job, In console output, we can see the job is executed in slave machine<br>

------------------------------------------------------------------------------------


# PIPELINE 

Implementing CI-CD  from the level of code.
This code is created using groovy script, and this file is also called as jenkins file.


Advantges:

As pipeline is implemented as code, it gives the developers the ability to upload into vesion controlling system from where they can edit and review the script.



Pipelines can accept interactive human input before continuning with specific stage in CI-CD


Ex: Before deployment into production environment, pipeline script can accept  approval from the delivery head and then continue.




Pipeline script support complex realtime scenario where we can implement conditional statements, loops etc.

Ex: If testing passes, we want to go to delivery. If its fails, we want to send automated emails.



Scripted pipeline syntax:<br>
-------------------------<br>
node ( 'master/slave')<br>
{<br>
         stage(' Stage in CI-CD')<br>
           {<br>
                   Groovy  code for implementing the stage<br>
           }<br>
}<br>




<br>
Install Build pipeline plugin<br>

Ex:<br>

Create new item ---  ScriptedPipeline<br>
select pipeline  --OK<br>
Pipeline tab,<br>

pipeline syntax<br>

Sample step - node: Allocate node<br>
 label - master<br>

Generate piplescript  -- copy the groovy code and paste in pipeline tab.<br>

In pipeline syntax <br>

Sample step - stage:Stage<br>
Stage name - Continuous Download<br>
Generate piplescript  -- copy the groovy code and paste in pipeline tab.<br>

-----<br>

In pipeline syntax <br>

Sample step - git:Git<br>
Repository URL - https://github.com/sunildevops77/maven.git<br>
Generate piplescript  -- copy the groovy code and paste in pipeline tab.<br>

-------------

Apply  --- Save --> Run the job<br>

2nd stage<br>
-----------------<br>
We need to run   'mvn package' command.<br>
This command can be executed as a shell script<br>


In pipeline syntax:<br>

Sample step - sh: Shell Script<br>
Stage name - mvn package<br>

Generate piplescript  -- copy the groovy code and paste in pipeline tab.<br>

Save and run.<br>




Step 3: Deployment<br>
We need to establish password less SSH connection between  Dev server and QA Server<br>
Connect to QA server using gitbash<br>

Set the password for ubuntu<br>
$ sudo passwd  ubuntu


Edit sshd_config  ( Password authentication -- yes)
$  cd /etc/ssh
$ sudo vim sshd_config

Go to insert mode

) change password authentication to yes

13) Save and quit :wq

14) Restart the service
$ sudo service ssh restart


15) Connect to dev server using gitbash and generate  ssh keys

$   ssh-keygen
Overwrite ?  n


18) copy the keys to QA server
ssh-copy-id  ubuntu@private_ip_qa_server
ssh-copy-id  ubuntu@172.31.47.36



Test are you able to connect to qa?
$ ssh ubuntu@172.31.47.36





$ exit   ( To come back to dev server)


Now, you can copy the files from dev server to QA server

Create a file in dev server
$ cat > file1
fdsfgfdsgfdsgd
Ctrl +d
$ 

To copy the file in QA server
Syntax:
$ scp  source   destination

$ scp  file1  ubuntu@172.31.47.36:/tmp/file2


file1  will be copied into qa server with the name file2

Lets check for the file, by connecting to qa server
$ ssh ubuntu@172.31.47.36
$ cd /tmp
$ ls
$ cat  file2
$ exit

++++++++++++++++++++++++++
Deployment is nothing but , copying the war file from dev server to qa server
Get the location of war file from log 

$ scp  /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war   ubuntu@172.31.47.36:/var/lib/tomcat8/webapps/qaenv.war

Get the groovy code of scp command

Sample Step - sh: Shell Script
Shell script --   copy the scp command which we have created


Generate the code and paste in pipeline script

Apply ---  save -- run

Deployment fails
Observe  the log file  ( permissions denied )

To give the permissions
Connect to qa server  using git bash
$ cd  /var/lib
$ ls -ld tomcat8

( Observation:   tomcat8  directory  -- others is not having write permissions )

$ sudo  chmod  -R  o+w   tomcat8/

Now run the job
+++++++++++++++++++=
Connect qa server and check


+++++++++++++++++++++++++++++++++
4th Stage: Continuous testing
In pipeline --  add a new stage


Shell script --   echo "Tesing Passed"

Generate the groovy code  and copy paste

Apply -- save-- run

+++++++++++++++++++++++++++++++++++
5th Stage : continuous delivery

In pipeline --  add  a new stage

Copy the code in the - continuousdeployment and change the qa_ipaddress to prod_Ip_address
Also change the context path  -  prodenv

( We need to establish password less ssh between devserver and prodserver)
( we should change tomcat8 permissions )

Connect to prod server using gitbash

Set the password for ubuntu
$ sudo passwd  ubuntu


Edit sshd_config  ( Password authentication -- yes)
$  cd /etc/ssh
$ sudo vim sshd_config

Go to insert mode

) change password authentication to yes

13) Save and quit :wq

14) Restart the service
$ sudo service ssh restart


15) Connect to dev server using gitbash and generate  ssh keys

$   ssh-keygen
Overwrite ?  n


18) copy the keys to Prod server
ssh-copy-id  ubuntu@private_ip_prod_server
ssh-copy-id  ubuntu@172.31.40.134

Test are you able to connect to prod?
$ ssh ubuntu@172.31.40.134
$ exit   ( To come back to dev server)

_______________

To give the permissions
Connect to prod server  using git bash
$ cd  /var/lib
$ ls -ld tomcat8

( Observation:   tomcat8  directory  -- others is not having write permissions )

$ sudo  chmod  -R  o+w   tomcat8/

Now run the job
Connect prod server and check

http://13.126.45.247:8080/prodenv/

+++++++++++++++++++++++++++++++++++++++++++++

### Script syntax for jenkins file
[jenkins syntax.txt](https://github.com/dayasanjay/jenkins/files/7969140/jenkins.syntax.txt)
