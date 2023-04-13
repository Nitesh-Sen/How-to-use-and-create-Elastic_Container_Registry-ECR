# What is Amazon Elastic Container Registry (ECR)?
Amazon Elastic Container Registry (ECR) is a managed AWS Docker registry service. Amazon ECR is a secure and reliable AWS service. Just like any other cloud computing service, we can scale it up or scale it down based on our requirements. Amazon ECR uses AWS Identity and Access Management (IAM) to enable resource-based permissions for private Docker repositories. Through the Docker command line interface (CLI) we can push, pull, and manage images.

 ## Why Amazon Elastic Container Registry (ECR)?
 - AWS ECR is highly secure, scalable and reliable.
 - It is highly cost effective and integrates well with other standard AWS services, which improves developer experience.
 - It’s secure as it transfers container images over HTTPS and automatically encrypts your images at rest.
 - Running registries close to the systems running the containers cuts deployment latency and reduces exposure to network outages.

## Task:- In Elastic Container Registry (ECR), create the Private Repository. Also, locally generate a Docker Image and pull in ECR. Then, under Elastic Container Service (ECS), use that image. 

### How to Create the Private ECR Repository
- Sign in your [Amazon console](https://aws.amazon.com/console/).
- Press key [Alt+S] and type ECR. Then click on [Elastic Container Registry](https://us-west-1.console.aws.amazon.com/ecr/home?region=us-west-1)
	-  Click on ``Get started`` to create the repository. <br /> 
	  <img alt="coding" width="700" src="https://github.com/Nitesh-Sen/Elastic_Container_Registry-ECS/blob/main/Images/2023-04-13_14-25.png"> <br /> 
	- Choose your Repository type ``Private`` and give name ``app``. <br />
	  <img alt="coding" width="700" src="https://github.com/Nitesh-Sen/Elastic_Container_Registry-ECS/blob/main/Images/2023-04-13_15-00.png">
	- Now scroll down and click on ``Create repository`` <br />
	   <img alt="coding" width="700" src="https://github.com/Nitesh-Sen/Elastic_Container_Registry-ECS/blob/main/Images/2023-04-13_14-38.png">
	- Now, private ECR repository is created. <br />
	  <img alt="coding" width="700" src="https://github.com/Nitesh-Sen/Elastic_Container_Registry-ECS/blob/main/Images/2023-04-13_14-40.png">
