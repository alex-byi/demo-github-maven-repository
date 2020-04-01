# Create library and deploy it to github

### First, get GitHub Personal access tokens from your github account

### Next, you need to find and edit settings.xml.  
* To find it, see the 
[Maven website.](https://maven.apache.org/settings.html)
* Edit file by adding next blocks:
```
  <activeProfiles>
    <activeProfile>github</activeProfile>
  </activeProfiles>

  <profiles>
    <profile>
      <id>github</id>
      <repositories>
        <repository>
          <id>central</id>
          <url>https://repo1.maven.org/maven2</url>
          <releases><enabled>true</enabled></releases>
          <snapshots><enabled>true</enabled></snapshots>
        </repository>
        <repository>
          <id>github</id>
          <name>GitHub OWNER Apache Maven Packages</name>
          <url>https://maven.pkg.github.com/OWNER/REPOSITORY</url>
        </repository>
      </repositories>
    </profile>
  </profiles>

  <servers>
    <server>
      <id>github</id>
      <username>USERNAME</username>
      <password>TOKEN</password>
    </server>
  </servers>
``` 

### Next, edit pom.xml 

* add next block to your pom.xml:
```
<distributionManagement>
   <repository>
     <id>github</id>
     <name>GitHub OWNER Apache Maven Packages</name>
     <url>https://maven.pkg.github.com/OWNER/REPOSITORY</url>
   </repository>
</distributionManagement>
```
### Finally, deploy your library

* Run mvn deploy to deploy your package to github

In command line you can see:
```
...

[INFO] --- maven-deploy-plugin:2.7:deploy (default-deploy) @ demo-github-maven-repository ---
Downloading from github: https://maven.pkg.github.com/alex-byi/demo-github-maven-repository/org/example/demo-github-maven-repository/1.0-SNAPSHOT/maven-metadata.xml
Uploading to github: https://maven.pkg.github.com/alex-byi/demo-github-maven-repository/org/example/demo-github-maven-repository/1.0-SNAPSHOT/demo-github-maven-repository-1.0-20200401.144112-1.jar
Uploaded to github: https://maven.pkg.github.com/alex-byi/demo-github-maven-repository/org/example/demo-github-maven-repository/1.0-SNAPSHOT/demo-github-maven-repository-1.0-20200401.144112-1.jar (2.7 kB at 877 B/s)
Uploading to github: https://maven.pkg.github.com/alex-byi/demo-github-maven-repository/org/example/demo-github-maven-repository/1.0-SNAPSHOT/demo-github-maven-repository-1.0-20200401.144112-1.pom
Uploaded to github: https://maven.pkg.github.com/alex-byi/demo-github-maven-repository/org/example/demo-github-maven-repository/1.0-SNAPSHOT/demo-github-maven-repository-1.0-20200401.144112-1.pom (871 B at 472 B/s)
...

[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
...
```
 


