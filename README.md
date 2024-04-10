

------------------------------------------------------------

## Demo Project:
* Create EKS cluster with eksctl 
## Technologiesused: 
* Kubernetes, AWS EKS, Eksctl, Linux


Project Description:

### Create EKS cluster using eksctl tool that reduces the manual effort of creating an EKS cluster

* Install eksctl
  * install eksctl command line tool 

* Next Step - Configure  AWS credentials to connect eksctl with your AWS account

* Create EKS cluster using command line


![MINGW64__c_Users_Rajib 06-05-2023 13_23_50](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/6c1d3647-02f9-42f2-bdc7-6f1ef29a2382)


![MINGW64__c_Users_Rajib 06-05-2023 13_23_55](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/3f0729db-e033-4a3a-8fe7-57477aad0c29)


## Demo Project:
* CD - Deploy to EKS cluster from Jenkins Pipeline 
## Technologiesused: 
* Kubernetes, Jenkins, AWS EKS, Docker, Linux 
## Project Description:

### Install kubectl inside Jenkins Container as root user


![6 - Deploy to EKS Cluster from Jenkins Pipeline _ TechWorld with Nana - Brave 22-05-2023 12_04_45](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/6f8569d8-aa8c-403a-aa63-9ed135a320dd)


### Install aws-iam-authenticator inside Jenkins Container
* download the aws-iam-authenticatior
* edit execute perrmisssion
* move the file to usr/local/bin
* execute the command using ```aws-iam-authenticator help```

![root@ubuntu-s-2vcpu-4gb-fra1-01_ ~ 07-05-2023 00_17_07](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/05d434bc-885f-4f25-9d1a-d8b67aeb6c11)


![root@ubuntu-s-2vcpu-4gb-fra1-01_ ~ 07-05-2023 00_17_03](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/950e9368-4511-46fc-b2cb-92412ca92994)


### Create kubeconfig file to connect to EKS cluster and add it on Jenkins server

* Make a configuration file in the digital ocean sublets 
* create config file command ```vim config``` in digitalOcean server as we can see in fig
* values we need to update
   * 1.  server endpoint - The Kubernetes API server is the "public endpoint" for taking a cluster.
   * 2. certificate-authority-data - The certificate authority info can be found locally in ```cat .kube/config ```
   * 3. cluster name


![root@ubuntu-s-2vcpu-4gb-fra1-01_ ~ 22-05-2023 13_21_08](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/e473e0a6-e962-4d2f-88d2-3a2f864c55f6)


####  copy it to the Jenkins container server.

* enter the Jenkins container as the user
* do ```cd ~ ``` then navigate to the home directory
* create .kube inside the jenkins home folder
* using docker copy command ``` docker cp config container id:var/jenkins_home/.kube/ ``` we can easily copy  the file

![root@ubuntu-s-2vcpu-4gb-fra1-01_ ~ 06-05-2023 20_36_17](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/99c4d885-fb15-4521-b389-31f8c0872214)

![root@ubuntu-s-2vcpu-4gb-fra1-01_ ~ 06-05-2023 20_42_03](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/ebe21fd3-cdeb-442f-8330-747641f00559)


* We can see that the kubeconfig file has been copied into Jenkins' home directory using the command ``` cat .kube/config  ```

### Add AWS credentials on Jenkins for AWS account authentication

 ![java-maven-app » Folder » Global credentials (unrestricted)  Jenkins  and 48 more pages - Profile 1 - Microsoft​ Edge 06-05-2023 22_40_12](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/68febc48-2c42-469d-9512-e74c61da18d8)


### Adjust Jenkinsfile to configure EKS cluster deployment 

* In the deploy stage, we are going to execute the shell command "kubectl create deployment, name of deployment, and image name."
* We are going to create a simple "nginx deployment."

* Inside the environment variable, set the access key ID and access secret key credentials.

![Jenkinsfile - java-maven-app - Visual Studio Code 06-05-2023 23_49_19](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/3b22d3f7-9fa8-4122-bc88-699455388ed2)

 
 
  * In the next step, add the commit and push the Jenkinsfile repository to remote repository.
* run the pipline in jenkins
* When we run the pipeline in Jenkins, we can see that the pipeline was successfully executed and that the logs for deployment were created.

![java-maven-app » deploy-on-k8s #3 Console  Jenkins  and 50 more pages - Profile 1 - Microsoft​ Edge 07-05-2023 00_20_04](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/2004f8c5-05a1-4c6e-891f-cb0dac7ba6d1)


![java-maven-app » deploy-on-k8s #3 Console  Jenkins  and 50 more pages - Profile 1 - Microsoft​ Edge 07-05-2023 00_19_56](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/755d39ef-8998-411f-9de2-451b5f8e7d64)


* We see that Ngnix pods are running.


![MINGW64__c_Users_Rajib 07-05-2023 00_19_35](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/79143a2d-830b-4900-8959-6311380e6fc3)


-----------------------------------------------------------------------

  
------------------------------------------------------------------------------
  
  
  ## Demo Project: 
  * Complete CI/CD Pipeline with EKS and AWS ECR 
  ## Technologiesused: Kubernetes, Jenkins, AWS EKS, AWS ECR, Java, Maven, Linux, Docker, Git 
  ## Project Description: 
  ### Create private ECR Repository

  ![Elastic Container Registry - Create Repository - Google Chrome 07-05-2023 19_39_45](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/77fca88c-8b6d-4350-8c8c-608515a5f764)



* Create Credential for ECR repository in Jenkins

 
 * get password from  ``` aws ecr get-login-password --region ap-southeast-1 ``` and username ``` AWS ```

 ![System » Global credentials (unrestricted)  Jenkins  and 51 more pages - Profile 1 - Microsoft​ Edge 07-05-2023 19_49_23](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/31bce19f-fe80-4987-aa77-b6f89eaa4932)


### Created Secret for AWS ECR Registry in EKS cluster and adjusted reference in Deployment file
 * Locally, on your computer: Create a docker registry secret for ECR

![MINGW64__c_Users_Rajib 07-05-2023 19_58_22](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/9fce5663-e994-4407-9159-8f77dd7518fe)


![MINGW64__c_Users_Rajib 07-05-2023 19_58_22 - Copy](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/5144587a-7195-4a52-a403-42413aae51cc)


### Adjust Jenkinsfile to build and push Docker Image to AWS ECR

* Modify the Jenkinsfile to reflect the changes. In the "build and push image" stage, change the credentials ID to ```ecr-credentials```. Set the repository URL as an environment variable named ```DOCKER_REPO``` and use it throughout the pipeline. Additionally, update the image name in the ```deployment.yaml file```. Ensure to set the ECR repository ```ECR_REPO_URL``` as an environment variable and pass it as a parameter. 

### So the complete CI/CD project we build has the following configuration:
* a.CI step:Increment version
* b.CI step: Build artifact for Java Maven application 
* c.CI step: Build and push Docker image to AWS ECR 
* d.CD step: Deploy new application version to EKS cluster 
* e.CD step: Commit the version update


### Execute Jenkins Pipeline

* As we can see, the pipeline has successfully been executed.

![complete-pipeline-ecr-eks  java-maven-app   Jenkins  and 51 more pages - Profile 1 - Microsoft​ Edge 07-05-2023 20_18_31](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/00fbf61d-f53e-4811-9a4d-159266190012)

* In our ECR repository, we can see a new image with increment version 1.1.3 appear here.

![Elastic Container Registry - Images - Google Chrome 07-05-2023 20_19_14](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/e09fa50d-6604-4e18-8ab8-ec8d7816fd3a)


*  We can see that pods and services are running.

![MINGW64__c_Users_Rajib 07-05-2023 20_19_31](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/557323b5-1def-4fc0-8425-5416bc6d967b)

![MINGW64__c_Users_Rajib 07-05-2023 20_26_16](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/03362771-01e0-4b91-9150-15feba4c5c9a)






