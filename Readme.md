## Amazon MWS API Java Client

Amazon provides MWS API [Java Client Libraries](https://developer.amazonservices.com/javaclients) in a way that is not friendly for Maven based projects.
I've tried to re-use [mws-client](https://mvnrepository.com/artifact/amazon/mws-client/1.0) in Maven Central, only to find that one was invalid for a long time. Finally, I chose to spent some time to build my own module and set the dependencies according to its third-party libraries. Feel free to use it.

## How to Use
```xml
<dependency>
  <groupId>com.github.ny83427</groupId>
  <artifactId>mws-java-client</artifactId>
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

## Disclaimer

I created this repository and deploy to Maven Central only in the purpose of convenience of the community. The copy right of the code belongs to Amazon, not myself. It's always OK to download the distribution in official website and set dependencies yourself if you have some concern on license or copy right issue.



