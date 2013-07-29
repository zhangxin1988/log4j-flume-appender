log4j-flume-appender
====================
include Log4jAppender/FailOverLog4jAppender/LoadBalancingLog4jAppender

Log4jAppender==>log4j.properties
log4j.rootLogger =INFO,a1,flume

# a1 console
log4j.appender.a1=org.apache.log4j.ConsoleAppender
log4j.appender.a1.layout=org.apache.log4j.PatternLayout

# flume
log4j.appender.flume=com.bj58.dsap.log4flume.Log4jAppender
log4j.appender.flume.Hostname=host
log4j.appender.flume.DirName=test
log4j.appender.flume.port=41414
log4j.appender.flume.layout=org.apache.log4j.SimpleLayout


FailOverLog4jAppender==>log4j.properties
log4j.rootLogger =INFO,a1,flume

# a1 console
log4j.appender.a1=org.apache.log4j.ConsoleAppender
log4j.appender.a1.layout=org.apache.log4j.PatternLayout


# flume
log4j.appender.flume=com.bj58.dsap.log4flume.FailOverLog4jAppender
log4j.appender.flume.Hosts=10.5.12.xxx:41414 10.5.12.xxx:41414
log4j.appender.flume.DirName=fail_test
log4j.appender.flume.layout=org.apache.log4j.PatternLayout


LoadBalancingLog4jAppender ==>log4j.properties
log4j.rootLogger =INFO,a1,flume

# a1 console
log4j.appender.a1=org.apache.log4j.ConsoleAppender
log4j.appender.a1.layout=org.apache.log4j.PatternLayout


# flume
log4j.appender.flume=com.bj58.dsap.log4flume.LoadBalancingLog4jAppender
log4j.appender.flume.Hosts=10.5.12.xxx:41414 10.5.12.xxx:41414
log4j.appender.flume.DirName=balance_test
log4j.appender.flume.Selector = RANDOM
log4j.appender.flume.layout=org.apache.log4j.PatternLayout

