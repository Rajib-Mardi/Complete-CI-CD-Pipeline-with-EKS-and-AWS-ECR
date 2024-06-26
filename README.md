 
  ### Demo Project: 
  * Complete CI/CD Pipeline with EKS and AWS ECR 
  ### Technologiesused: 
  * Kubernetes, Jenkins, AWS EKS, AWS ECR, Java, Maven, Linux, Docker, Git 
  ### Project Description: 
  ####  Create private ECR Repository

  <img src="https://github.com/Rajib-Mardi/Complete-CI-CD-Pipeline-with-EKS-and-AWS-ECR/assets/96679708/6cdd5b2f-1496-42f4-a63e-6573408c59b5" width="800">

![240625046-77fca88c-8b6d-4350-8c8c-608515a5f764](https://github.com/Rajib-Mardi/Complete-CI-CD-Pipeline-with-EKS-and-AWS-ECR/assets/96679708/6cdd5b2f-1496-42f4-a63e-6573408c59b5)



* Create Credential for ECR repository in Jenkins

 
 * get password from  ``` aws ecr get-login-password --region ap-southeast-1 ``` and username ``` AWS ```

<img src="https://github.com/Rajib-Mardi/Complete-CI-CD-Pipeline-with-EKS-and-AWS-ECR/assets/96679708/bfcfd338-29ae-40b9-b698-43256aabc851" width="800">



#### Created Secret for AWS ECR Registry in EKS cluster and adjusted reference in Deployment file
 * Locally, on your computer: Create a docker registry secret for ECR


<img src="https://github.com/Rajib-Mardi/Complete-CI-CD-Pipeline-with-EKS-and-AWS-ECR/assets/96679708/de015aa1-62f1-4bc8-b7d0-0aac5d1f0531" width="800">

<img src="https://github.com/Rajib-Mardi/Complete-CI-CD-Pipeline-with-EKS-and-AWS-ECR/assets/96679708/1b706499-b813-457a-87cf-a2edc619031c" width="800">


#### Adjust Jenkinsfile to build and push Docker Image to AWS ECR

* Modify the Jenkinsfile to reflect the changes. In the ```build and push image``` stage, change the credentials ID to ```ecr-credentials```. Set the repository URL as an environment variable named ```DOCKER_REPO``` and use it throughout the pipeline. Additionally, update the image name in the ```deployment.yaml file```. Ensure to set the ECR repository ```ECR_REPO_URL``` as an environment variable and pass it as a parameter. 

#### So the complete CI/CD project we build has the following configuration:
* a.CI step:Increment version
* b.CI step: Build artifact for Java Maven application 
* c.CI step: Build and push Docker image to AWS ECR 
* d.CD step: Deploy new application version to EKS cluster 
* e.CD step: Commit the version update


#### Execute Jenkins Pipeline

* As we can see, the pipeline has successfully been executed.

 <img src="https://github.com/Rajib-Mardi/Complete-CI-CD-Pipeline-with-EKS-and-AWS-ECR/assets/96679708/9895ce5c-8ad0-4cc3-99fc-10f6cd2dd44e" width="800">



* In our ECR repository, we can see a new image with increment version 1.1.3 appear here.


 <img src="https://github.com/Rajib-Mardi/Complete-CI-CD-Pipeline-with-EKS-and-AWS-ECR/assets/96679708/2d963870-834f-43e4-a446-403b0018bb7b" width="800">




*  We can see that pods and services are running.


 <img src="https://github.com/Rajib-Mardi/Complete-CI-CD-Pipeline-with-EKS-and-AWS-ECR/assets/96679708/cb0413c3-e95c-497c-966e-f6cd84778c5b" width="800">


 <img src="https://github.com/Rajib-Mardi/Complete-CI-CD-Pipeline-with-EKS-and-AWS-ECR/assets/96679708/15cbc34f-4e75-484f-8178-e563d9e341b9" width="800">








