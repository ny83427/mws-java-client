## Amazon MWS API Java Client

Amazon provides MWS API [Java Client Libraries](https://developer.amazonservices.com/javaclients) in a way that is not friendly for Maven based projects.
I've tried to re-use [mws-client](https://mvnrepository.com/artifact/amazon/mws-client/1.0) in Maven Central, only to find that the repository url is 
invalid. Finally, I had to spent some time to build my own module and set the dependencies according to its third-party libraries.

## How to Use

As I didn't deploy this library to Maven Central but to our own private Nexus only, you need to declare repositories in your POM file:

```xml
<repositories>
  <repository>
    <id>releases</id>
    <url>http://nexus.ibport.com:8082/nexus/content/repositories/releases</url>
  </repository>
</repositories>
```

And then add the dependency:

```xml
<dependency>
  <groupId>com.amazonaws</groupId>
  <artifactId>mws</artifactId>
  <version>1.0</version>
</dependency>
```

## Regarding log4j.properties

I didn't keep it as the log level is too verbose. You may create your own `log4j.properties` under classpath based on lines in the below:
```properties
log4j.rootLogger=DEBUG, APP
#log4j.appender.A1=org.apache.log4j.ConsoleAppender
#log4j.appender.A1.layout=org.apache.log4j.PatternLayout

log4j.appender.APP=org.apache.log4j.RollingFileAppender
log4j.appender.APP.File=client.log
log4j.appender.APP.layout=org.apache.log4j.PatternLayout

# Print the date in ISO 8601 format
log4j.appender.APP.layout.ConversionPattern=%d [%t] %-5p %c - %m%n

# Adjust to see more logging
log4j.logger.com.amazonaws.mws=DEBUG
log4j.logger.httpclient=DEBUG
```

## Future Work

It might be helpful to other developers if we deploy this to Maven Central. However, there might be some copyright issue.
Let's check it out in the future.



