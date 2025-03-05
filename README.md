# simple-java-maven-app
Maven project. Here's an overview of its file structure:

src/main/java/: Contains the Java source code.
src/main/resources/: Holds configuration files and other resources.
target/: The default directory where Maven outputs compiled classes and built JAR files.
Dockerfile: Defines instructions to build a Docker image for the application.
README.md: Provides information about the project.
pom.xml: The Maven Project Object Model file, which manages project dependencies and build configurations.

Prerequisites
Make sure you have the following installed on your system:

Git (to clone the repository)
Java (JDK 8 or higher) (to run the application)
Maven (to build and manage dependencies)
Docker (if you want to run it inside a container)

manual execution:
--------------------------------------------------------------------------------------------------
steps:
git clone https://github.com/ganesh-redy/java-jar.git
cd java-jar


mvn clean package

After this, you should see a .jar file inside target/, something like: target/java-jar-1.0-SNAPSHOT.jar

Run the JAR File To test the application, execute: java -jar target/java-jar-1.0-SNAPSHOT.jar(x)
Run Using Docker(preferred): 
docker build -t java-jar-app .
docker run -p 8081:8081 java-jar-app
you can access it at http://localhost:8081

Check Code Quality with SonarQube:
docker run -d --name sonar -p 9000:9000 sonarqube
mvn sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dsonar.token=YOUR_GENERATED_TOKEN


jenkins:
--------------------------------------------------------------------------------------------------
 Set Up Jenkins Pipeline Job
Go to Jenkins Dashboard → New Item → Pipeline.
Enter Job Name (e.g., Java-Maven-SonarQube-Pipeline).
Select Pipeline and click OK.
Scroll down to Pipeline → Definition: Pipeline script from SCM.
Select Git, enter the repository URL (https://github.com/Mohammedirshaq/java-jar.git).
Branch: main (or your branch name).
Script Path: Jenkinsfile.
Save and Build Now.


Configure Jenkins Credentials for SonarQube
Instead of hardcoding the SonarQube token, store it securely in Jenkins:

Go to Jenkins Dashboard → Manage Jenkins → Manage Credentials.
Under Global credentials, click Add Credentials:
Kind: Secret text
Scope: Global
Secret: (Paste the SonarQube token)
ID: sonar-token
Click OK.

Run the Jenkins Job
Go to Jenkins Dashboard → Select your Pipeline.
Click Build Now.
If successful:
The project automatically appears in SonarQube (http://localhost:9000/projects).
Code analysis is performed.


