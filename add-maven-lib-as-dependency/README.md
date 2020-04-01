# Add maven lib from github as dependency

### Add dependency in pom.xml
* Add next block to pom.xml:
```
<dependencies>
    <dependency>
        <groupId>org.example</groupId>
        <artifactId>test</artifactId>
        <version>1.0.0-SNAPSHOT</version>
    </dependency>
</dependencies>
```
In my case, I added:
```
<dependencies>
    <dependency>
        <groupId>org.example</groupId>
        <artifactId>demo-github-maven-repository</artifactId>
        <version>1.0-SNAPSHOT</version>
    </dependency>
</dependencies>
```

### Import required package in your classes

```
import org.example.github.maven.repository.WrongCalc;
```

### And use it
```
System.out.println(WrongCalc.sum(2, 2));
```


