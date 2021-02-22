# Programming Project 1
## Understanding Git
If you're unfamiliar with version control systems, especially Git, please consult the [Git Handbook](https://guides.github.com/introduction/git-handbook/) and some of the additional resources it provides.

## Setting up your local environment
1.	[Install JDK](https://www.oracle.com/java/technologies/javase-jdk15-downloads.html)  
  a.	Please check whether or not the environment variables are set properly.

2.	[Install Spark](https://spark.apache.org/downloads.html)  
  a.	Please install version 3.0.1 with Hadoop 2.7.  
  b.	After the installation, you may need to set up the environment variables properly.  
  c.	To test whether or not everything runs properly, open a terminal and type `spark-shell` to see if you can run it. Now that you are in the Scala interpreter, you can execute Scala code here. For example, you can try `println(“Hello World!”)`. You can exit the shell by typing `:q`.  
  d.	Tip: In the Spark shell, you can test segments of Scala codes before you write them in the file. It's a very convenient way to learn Scala and Spark.   
  
3.	[Install SBT](https://www.scala-sbt.org/download.html)  
  a.	SBT is a builder for Scala programs.  
  b.	Check if the environment variables are set properly.  
  
## Cloning the project_1 repository
This is a template repository. You can duplicate the repository, renaming it and adjusting your own settings, but cannot directly clone it and push to its **origin/main** branch. Create your own repository by selecting the green **Use this template** button. You'll be submitting the link to the respository you created (more on that later). Once you have your own repository, you can clone it to your local machine.

## Validating your environment
Let's build and execute **project_1**.  
1. Navigate to the project root and type `sbt clean package` to build the project's **.jar** file.  
2. Run the following command:
```
// Linux
spark-submit --class project_1.main --master local[*] target/scala-2.12/project_1_2.12-1.0.jar

// Unix
spark-submit --class "project_1.main" --master "local[*]" target/scala-2.12/project_1_2.12-1.0.jar
```
3. Upon successful execution, you should see the message below. Note that `string`, `difficulty`, and `#trials` are the arguments you'll be passing in.
```
Usage: project_1 string difficulty #trials
```

## Setting up GCP
1. Sign up for an account **with your BC email** on [Google Cloud Platform](https://cloud.google.com).  
2. Apply [here](https://google.secure.force.com/GCPEDU?cid=qK5GptnHvOd1Azky9STHgTXZKL0TQBk8k%2BgpC7W6XDRhxyd1yHT7DqKeE2yLVLeQ) for the course's pre-approved credits. GCP will request that you verify your email address first.  
3. Once you verify your email address, you'll receive an email allowing you to redeem your credits. It links to a page where you can redeem using the coupon code GCP provides you.  
4. You should now have $50 in credit. You can verify this by doing the following:  
  a. Open the navigation menu in the top left corner.  
  b. Navigate to **Billing**.  
  c. Select **bc.edu** as your organization and open the **Billing Account for Education** account.  
  d. On the overview page for this billing account, there's a **Promotional credits** box towards the bottom right of the page. The balance should be $50.  
5. Use your credits judiciously. Creating large clusters, using complex features like Jupyter Notebook, or forgetting to terminate clusters after use are some activities that quickly consume credits. While you have $50 in credit, you shouldn't expect to use more than $10 for the course.  

## Creating a GCP project
1. Select the **bc.edu** organization name in the top bar and then the **New Project** button in the top right corner of that menu.  
2. For the project name, we recommend that you follow the `bcusername-csci3390-project` convention, e.g. `smith-csci3390-project1`.  
3. Leave **bc.edu** as the organization and choose **bc.edu/Learning/Student** (which you can access through **Browse**) as the location.  
4. Creating the project should bring you to the project overview page. In the search bar at the top, search for "dataproc" and select the **Dataproc** product.  
5. Enable the Cloud Dataproc API.  
6. Select the **Create Cluster** button and configure your cluster the following way:  
  a. Cluster name `bcusername-csci3390-cluster`, e.g. `smith-csci3390-cluster`.  
  b. Version image 2.0 with Debian or Ubuntu (it will look like `2.0-debian10`).  
  c. In the `Customize cluster` page, check the box in the `Scheduled deletion` section that says "Delete after a cluster idle time period without submitted jobs" and specify a 2 hour timeout. This will terminate the cluster in case you forget to manually.  
7. To execute the project's **.jar** file, you'll need to upload it somewhere accessible to the cluster. This can be accomplished by creating a [GCP storage bucket](https://console.cloud.google.com/storage). Name it `bcusername-csci3390-bucket`, e.g. `smith-csci3390-bucket`. Leave the rest of the settings on their default.  
8. Upload the **.jar** file located in **target/scala-2.12** in your project directory.  
9. Back in the **Dataproc** console, select the **Submit Job** button on the **Jobs** page.  
10. Submit a job with the following configuration:  
  a. Select the cluster you created for **Cluster**.  
  b. `Spark` job type.  
  c. `project_1.main` for the main class.  
  d. `gs://your-bucket-name/project_1_2.12-1.0.jar` for the **.jar** file.  
  e. A value of 1 for maximum restarts per hour.  
11. Upon successful execution, you should see `Usage: project_1 string difficulty #trials` as the job output. Cheers to successfully configuring your cloud environment.

## Bitcoin mining with Spark
