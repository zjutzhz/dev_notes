1. list the dependency [[REf]](http://stackoverflow.com/questions/34723817/how-to-output-a-simple-list-of-maven-dependencies)
```shell
mvn org.apache.maven.plugins:maven-dependency-plugin:2.1:list -f sample.pom -DoutputFile="..."
```

2. skip java doc build[[Ref]](http://stackoverflow.com/questions/7412016/how-can-i-disable-the-maven-javadoc-plugin-from-the-command-line)
```xml
<properties>
    <maven.javadoc.skip>true</maven.javadoc.skip>
</properties>
```
