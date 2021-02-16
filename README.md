# Programming Project 1
## Understanding Git
If you're unfamiliar with version control systems, especially Git, please consult the [Git Handbook](https://guides.github.com/introduction/git-handbook/) and some of the additional resources it provides.

## Setting up your local environment
1.	[Install JDK](https://www.oracle.com/java/technologies/javase-jdk15-downloads.html)  
  a.	Please check whether or not the environment variables are set properly.

2.	[Install Spark](https://spark.apache.org/downloads.html)  
  a.	Please install the 3.0.1 version with Hadoop 2.7.  
  b.	After the installation, you may need to set up the environment variables properly.  
  c.	To test whether or not everything runs properly, open a terminal and type `spark-shell` to see if you can run it. Now that you are in the Scala interpreter, you can execute Scala code here. For example, you can try `println(“Hello World!”)`. You can exit the shell by typing `:q`.  
  d.	Tip: In the Spark shell, you can test segments of Scala codes before you write them in the file. It is a very convenient way to learn Scala and Spark.   
  
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
