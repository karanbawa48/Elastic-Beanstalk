# What is Elastic Beanstalk
Elastic Beanstalk is a service for deploying and scaling web applications and services. Upload your code and Elastic Beanstalk automatically handles the deployment—from capacity provisioning, load balancing, and auto scaling to application health monitoring.

## Deploy a docker container by Elastic Beanstalk with CI/CD.
In this tutorial we will deploy a **Docker container** by **Elastic Beanstalk**. we will use **Github** as a source code repo and AWS pipeline for **CI/CD**. 
## **Prerequisite**

 - **GitHub** account.
 - sample app (we will deploy a simple static website by dockerfile)
 - AWS Account
 ### **Step 1 — Setup AWS Elastic Beanstalk**
- **First click on Create Application**. 
(you will see the following page and fill details according. we are using **test** as the application name. use tags. For **Platform** we are docker (as we are deploying a docker container). In **Platform branch**. you can either use *docker on EC2 *or *ECS*. In Application code, upload your code. here you can upload from local or you can use S3 as well.
**![](https://lh3.googleusercontent.com/kBbcqDYe3wKQ5erZn__t8qzkbBrGCyGzxMksDEbJbeRdeGkVUyLcAxl3XI3A0Jgcn9-lcQulIIewVP0KKy0g4H9E4KevYgroA8ptLItvp_uJ_rAxOsrtdXXxusqnbjSHokmbgqQuWKbsDQjQ3CTZBso3Sh-DMT66c8VnTNjniAy4rDFf_wNDz-Xo_g)**
- After Providing required details. click  Create Application.
(The Application will start deploying you can see the events what  Elastic Beanstalk is doing at the backend. )
**![](https://lh6.googleusercontent.com/CRYZH3G7n6qBYXakg4Sy17543-U6ZUajvzanVeMLsmxNO7-xMzOAoy2tvPx0ajEJHvvQMrEBVRLLVMwrDKJHfi0HwFOe7PtFsXZ0Q7AsSh4enovkBMdmWrUHuSUrT0KzWFJidhUrNZ-qwhHQTRBv9l10WcxgCKc3SFDefW-LiUhOW7zS42Xo4ZW57w)**
*note: It'll take some time*
- The Env will be created. If the status is Green. EB will give a URL, that will redirect you to your application. 
- **![](https://lh6.googleusercontent.com/dvPaC0t-d0Q5DaqOD6XinqPv6tEhmxU6F-KGF8JTPIbT9RWaq2yYIdCQLgkmQDPnTOy4RhjD4GJVkVvHEwnzRbWrRYBsJZktDYG6YRpZrS6zLB7y18tDSRFM74gogad-gexMzpHS6gCvQTa8ZVV_n8Tu6bN7O7Hw9hgQhhtT0MXj4wPbrinrO3bLjQ)**
 ### **Step 2 — Create  AWS code pipeline**
 - **First click on go to AWS Developer tools and select Code pipeline**.
- Now click on Create Pipeline.
- Provide pipeline's name.
- A role will be created on behalf of you for this pipeline	or you can give your own custom role as well.
- Click Next
- **![](https://lh3.googleusercontent.com/dufjJZR8EA0qzyrSpf_VfzKUvC2wWPY8pszBzZe1KTiLt5ERsqIoTUlf-_ScwGO48KPXwdMapx3WuujlhLDVgFINS8um_1N4yeS_lc6T0wi8LbL2xiY3LUqDsGllM8aHK1SeKS1zWmOSu6qS7qpGOOyc_Dek7ubx4ctDbxx6Jp78FvWb1NlN4yNAMQ)**	
 - **Now  Add source stage**.
- here you will chose from where you want to take you source code. We are using **GitHub Version2**

- ![](https://lh5.googleusercontent.com/LEdslmLiaT5KPMI6glbyvfyL8t_PxoUYyQd36uriCcLzvm77h8OSEKNfxj5u5zFTfssB8gk8mLZjcYeS_Mlt7yTufKhrX2UzXlXFtuVKmICrJ8u7xZ-yiqVegZUy5FmYPVYLul26yuC6YZzTUgsADS8VDwR9TbuMVAl8hTqnoRhGYQ96YHKpMRxJMw)**
## Create a connection with Github by clicking on **connect with Github**. 
- A pop window will open as shown in the image below. Enter any name for connection. click on *Connect to GitHub*
- Create a GitHub app 
(GitHub Apps create a link for your connection with GitHub.)
- Log in with your github account where you have your source code.
- In **Repository access** . 
(you can give access to all repository. But good practice is to give minimum access)
- Select you Repo from Only select repositories and Click on  **Save**.
- ****![](https://lh6.googleusercontent.com/W_-8GYXxnsJBTurR52WPYCmrWNJluaBO25h9BmAA3_B3iLUBo1qiETYXqbZXP08XJ60LPzXI_js8vusIrdw8GCTorgo35LNTKLYfZyI_-ni8wh0RnXElIp79PcHgJ7fuZ7gvLq3WjzW-TdHbTHpbj2vgBslH7y27i4CD3NG0m1JXdr_Qii2X2wrjbA)****
- Now your App will be created and Click on **connect**.
	   The pop up window will auto close and looks like :
	   **![](https://lh4.googleusercontent.com/kYaAM-dd6a02mjauHgQzLPBPjkSJ-62DFudrE4umOMUWH6WyAciJ116h6MfggQ777fXw8hTZB2kKGUY6XIzRXwgDtu34hpHFbCShWbeIl_p0zHkAg5W2chm9rTivD7lUUI84-P7ZBOTWoUW7igNQldw2woVsILzttIsgnTEEHLdmQTUg92S4zabP_A)**
	   - Select the Repo and Branch.
	   - Click on **Next**.
	   - **Spike the build part**
	   - -**Add deploy stage**
	   - **![](https://lh3.googleusercontent.com/IQcjBIB3X1hQDyWMQcfFJgJE73lUclFB5ECVrNZIkmyuE4V2p_tjsgtvvCrWdwdCxkZGqt05rvGYsTDV1C-Mi3vTDZSJeBfxh1dzJIgZ7Bd-9ZqEtp2PEPJCwXwjiACJmar8RkuRlHXTaz2jtdZPM9Q9YskAwIbKvPAHXV0_wu16pHWh9ysEpwO8Hg)**
	  - Here select Elastic Beanstalk as Deployment provider.
	   - select region, where you EB application is running.
	   - select **application** in **Application name**.	
	   -  select **Environment** in **Environment name**. and click on Next.
	   - Review your Pipeline. if all good, click on create pipeline.
	   - **![](https://lh6.googleusercontent.com/rmTFJHCfBABtyiRID-F2rWfwumwP2KiJtvCt8TmMduqM4OkSNm7vfEklyH0Wst4ZavQQOv7ZDtHDjFE81HQD49ERTfWzPvXdrjacu0t9SUQQx9zOnK27_BXhJQJoope-gNUQgM71JyXHZnLyWvGDgUQHg5bdwWL68bJC6dWOOIKKYIeu-r3IIqTZOA)**
	   The pipeline will be created and will start deploying your application
	  
	# Blue Green Deployment

	   
