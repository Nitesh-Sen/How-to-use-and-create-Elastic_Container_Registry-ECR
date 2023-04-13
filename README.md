
## What is Amazon Elastic Container Registry (ECR)?
Amazon Elastic Container Registry (ECR) is a managed AWS Docker registry service. Amazon ECR is a secure and reliable AWS service. Just like any other cloud computing service, we can scale it up or scale it down based on our requirements. Amazon ECR uses AWS Identity and Access Management (IAM) to enable resource-based permissions for private Docker repositories. Through the Docker command line interface (CLI) we can push, pull, and manage images.

 ## Why Amazon Elastic Container Registry (ECR)?
 - AWS ECR is highly secure, scalable and reliable.
 - It is highly cost effective and integrates well with other standard AWS services, which improves developer experience.
 - It’s secure as it transfers container images over HTTPS and automatically encrypts your images at rest.
 - Running registries close to the systems running the containers cuts deployment latency and reduces exposure to network outages.

# Task:- 
- [Create the Private Amazon ECR Repository](#creating-an-ecr-repository). 
- Build a **Docker Image**  of **Apache container** and configure web page, add this data ``Hello From ECS`` in web page. Then, Pull that **Docker Image** to Amazon ECR.
	- [Create a **Dockerfile**](create-an-dockerfile)
	- Build the image    
-   Create a **Cluster** in Amazon Elastic Container Service (ECS). And in the **Task Defination** define that docker image. And run that task with that Docker Image.  
-   Finally, search the DNS in your Browser and check your web page show this -> ``Hello From ECS``


### Must Have

-   [AWS Credentials](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html)  with permissions to interact with ECR.
-   [Docker installation in localy for Ubuntu OS](https://docs.docker.com/engine/install/ubuntu/). 
	 Docker installing for other operating system, click [here](https://docs.docker.com/get-docker/).
-   The  [AWS CLI installed locally](https://aws.amazon.com/cli/). And configure the credentials.

### Creating an ECR Repository
- Sign in your [Amazon console](https://aws.amazon.com/console/).
- Press key [Alt+S] and type ECR. Then click on [Elastic Container Registry](https://us-west-1.console.aws.amazon.com/ecr/home?region=us-west-1)
#### Configuring Your Repository
-  Click on ``Get started`` to create the repository. <br /> 
	  <img alt="coding" width="700" src="https://github.com/Nitesh-Sen/Elastic_Container_Registry-ECS/blob/main/Images/2023-04-13_14-25.png"> <br /> 
- Choose your Repository type ``Private`` and give name ``app``. <br />
	  <img alt="coding" width="700" src="https://github.com/Nitesh-Sen/Elastic_Container_Registry-ECS/blob/main/Images/2023-04-13_15-00.png"> <br />
- Select any of the other options you need **Optional**:

	-   _Tag immutability_  which prevents the same tag from being pushed twice and overwriting a previous version of the tag.
	-   _Scan on push_  which ensures that images will be scanned for security vulnerabilities each time a new tag is pushed.
	- _KMS encryption which allows us to use AWS Key Management Service (KMS) to encrypt the images in this repository. <br />
- Now scroll down and click on ``Create repository`` <br />
	   <img alt="coding" width="700" src="https://github.com/Nitesh-Sen/Elastic_Container_Registry-ECS/blob/main/Images/2023-04-13_14-38.png">
- Now, private ECR repository is created. <br />
	  <img alt="coding" width="700" src="https://github.com/Nitesh-Sen/Elastic_Container_Registry-ECS/blob/main/Images/2023-04-13_14-40.png">

 ### Create And Build the image. Then push that image to ECR Repository
 #### Create an Dockerfile.
 - Run this command to create a directory  and go in that directory. ``$ mkdir ~/Docker && cd ~/Docker``
- Create a file with name **Dockerfile** and add this data. 
```
	FROM ubuntu:22.04

	RUN apt update && apt install -y apache2

	ENV APACHE_RUN_USER www-data
	ENV APACHE_RUN_GROUP www-data
	ENV APACHE_LOG_DIR /var/log/apache2
	ENV APACHE_RUN_DIR /var/www/html

	RUN echo "<font size = "20" color="green"><b><u>Hello From ECS ;)</u></b></font><br />" > /var/www/html/index.html

	ENTRYPOINT ["/usr/sbin/apache2"]
	CMD ["-D", "FOREGROUND"]
```
 &nbsp; &nbsp; &nbsp; &nbsp; <img alt="coding" width="700" src="https://github.com/Nitesh-Sen/Elastic_Container_Registry-ECS/blob/93bb453df7baeefc053fa4a539c007d2b7f39ccb/Images/Image19-18-39_2023-04-13.png">
