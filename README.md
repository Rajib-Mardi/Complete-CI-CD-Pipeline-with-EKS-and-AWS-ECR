
------------------------------------------------------------------------------
  
  
  ### Demo Project: 
  * Complete CI/CD Pipeline with EKS and AWS ECR 
  ### Technologiesused: 
  * Kubernetes, Jenkins, AWS EKS, AWS ECR, Java, Maven, Linux, Docker, Git 
  ### Project Description: 
  ####  Create private ECR Repository

![240625046-77fca88c-8b6d-4350-8c8c-608515a5f764](https://github.com/Rajib-Mardi/Complete-CI-CD-Pipeline-with-EKS-and-AWS-ECR/assets/96679708/6cdd5b2f-1496-42f4-a63e-6573408c59b5)



* Create Credential for ECR repository in Jenkins

 
 * get password from  ``` aws ecr get-login-password --region ap-southeast-1 ``` and username ``` AWS ```

![240630433-31bce19f-fe80-4987-aa77-b6f89eaa4932](https://github.com/Rajib-Mardi/Complete-CI-CD-Pipeline-with-EKS-and-AWS-ECR/assets/96679708/bfcfd338-29ae-40b9-b698-43256aabc851)

#### Created Secret for AWS ECR Registry in EKS cluster and adjusted reference in Deployment file
 * Locally, on your computer: Create a docker registry secret for ECR

![MINGW64__c_Users_Rajib 07-05-2023 19_58_22](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/9fce5663-e994-4407-9159-8f77dd7518fe)


![MINGW64__c_Users_Rajib 07-05-2023 19_58_22 - Copy](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/5144587a-7195-4a52-a403-42413aae51cc)


#### Adjust Jenkinsfile to build and push Docker Image to AWS ECR

* Modify the Jenkinsfile to reflect the changes. In the "build and push image" stage, change the credentials ID to ```ecr-credentials```. Set the repository URL as an environment variable named ```DOCKER_REPO``` and use it throughout the pipeline. Additionally, update the image name in the ```deployment.yaml file```. Ensure to set the ECR repository ```ECR_REPO_URL``` as an environment variable and pass it as a parameter. 

#### So the complete CI/CD project we build has the following configuration:
* a.CI step:Increment version
* b.CI step: Build artifact for Java Maven application 
* c.CI step: Build and push Docker image to AWS ECR 
* d.CD step: Deploy new application version to EKS cluster 
* e.CD step: Commit the version update


#### Execute Jenkins Pipeline

* As we can see, the pipeline has successfully been executed.

![complete-pipeline-ecr-eks  java-maven-app   Jenkins  and 51 more pages - Profile 1 - Microsoft​ Edge 07-05-2023 20_18_31](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/00fbf61d-f53e-4811-9a4d-159266190012)

* In our ECR repository, we can see a new image with increment version 1.1.3 appear here.

![Elastic Container Registry - Images - Google Chrome 07-05-2023 20_19_14](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/e09fa50d-6604-4e18-8ab8-ec8d7816fd3a)


*  We can see that pods and services are running.

![MINGW64__c_Users_Rajib 07-05-2023 20_19_31](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/557323b5-1def-4fc0-8425-5416bc6d967b)

![MINGW64__c_Users_Rajib 07-05-2023 20_26_16](https://github.com/Rajib-Mardi/Kubernetes-on-AWS-EKS/assets/96679708/03362771-01e0-4b91-9150-15feba4c5c9a)






