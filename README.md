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
  
