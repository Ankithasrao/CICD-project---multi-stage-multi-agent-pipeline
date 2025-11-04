# CICD-project-1-using-Docker-as-slave-deploy-applications-to-k8s-using-Argo-CD-in-GitOps-way.
Install Jenkins, configure Docker as slave, set up cicd, deploy applications to k8s using Argo CD in GitOps way.

#### Step 1 :  AWS EC2 Instance
#####  *  Go to AWS Console
##### *  Instances(running)
##### *  Launch instances

<img width="1988" height="1194" alt="image" src="https://github.com/user-attachments/assets/b767dcde-61c5-456a-ae33-369f65aaa1f6" />

#### Step 2 : Install Jenkins.
-   ##### Java (JDK)
  
#### Run the below commands to install Java and Jenkins
##### Install Java

```
sudo apt update
sudo apt install openjdk-17-jre
```
##### Verify Java is Installed

```
java -version
```
##### Now, you can proceed with installing Jenkins

```
curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```
##### **Note: ** By default, Jenkins will not be accessible to the external world due to the inbound traffic restriction by AWS. Open port 8080 in the inbound traffic rules as show below.

- ###### EC2 > Instances > Click on
- ###### In the bottom tabs -> Click on Security
- ###### Security groups
- ###### Add inbound traffic rules as shown in the image (you can just allow TCP 8080 as well, in my case, I allowed All traffic).

<img width="2374" height="396" alt="image" src="https://github.com/user-attachments/assets/c9a46139-df0d-4038-b1d4-3574758289c9" />

#### Step 3 : Login to Jenkins using the below URL
##### http://:8080 [You can get the ec2-instance-public-ip-address from your AWS EC2 console page]

##### Note: If you are not interested in allowing All Traffic to your EC2 instance 
- Delete the inbound traffic rule for your instance  
- Edit the inbound traffic rule to only allow custom TCP port 8080

##### After you login to Jenkins, - Run the command to copy the Jenkins Admin Password - sudo cat /var/lib/jenkins/secrets/initialAdminPassword - Enter the Administrator password


<img width="2582" height="1192" alt="image" src="https://github.com/user-attachments/assets/ed493d2f-8157-4991-8393-ccfe609469c4" />

###### Click on Install suggested plugins

<img width="2582" height="1192" alt="image" src="https://github.com/user-attachments/assets/bc21f68f-5695-4d7a-bb96-d489b7041c7c" />

###### Wait for the Jenkins to Install suggested plugins


<img width="2582" height="1192" alt="image" src="https://github.com/user-attachments/assets/c74e8002-ce4d-4ffb-b500-714fb808dcc4" />

###### Create First Admin User or Skip the step [If you want to use this Jenkins instance for future use-cases as well, better to create admin user]


<img width="1980" height="1232" alt="image" src="https://github.com/user-attachments/assets/abe890d3-38a6-423f-9032-da5f4c7e492e" />

##### Jenkins Installation is Successful. You can now starting using the Jenkins


<img width="1980" height="1232" alt="image" src="https://github.com/user-attachments/assets/be960f3a-e1bb-47e7-a30e-99c1161ef9e0" />





