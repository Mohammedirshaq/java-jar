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

