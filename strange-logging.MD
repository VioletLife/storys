# 神奇的日志
将log4j日志级别设置为INFO，在tomcat启动的过程中，还是会出现DEBUG级别的日志，现象为:在tomcat启动的过程中先打印DEBUG日志，等待启动完成后，开始INFO日志，说明工程中的级别其实是起作用了的，只是起作用的时机，比DEBUG的晚。因此可以断定日志时tomcat打印的，与工程无关，那么tomcat的日志又是咋回事呢?
Tomcat 日志部分文档[Tomcat 7 Logging](https://tomcat.apache.org/tomcat-7.0-doc/logging.html)
从文档中可以看到:Tomcat 的日志使用的Apache Commons Logging实现，只不过私有内置的方式进行实现，日志级别为:SEVERE, WARNING, INFO, CONFIG, FINE, FINER, FINEST or ALL，发现其中没有DEBUG。默认的是FINE。如果我们把FINE调整为INFO，再重新启动的话，就发现Tomcat启动不会打印DEBUG日志了。因此推测:FINE日志级别和LOG4J的DEBUG级别同等。
日志在开发的过程中有用，部署到正式环境后，**大量的日志输出会导致性能下降(比如磁盘，比如CPU)**，因此在正式环境关闭就好了。


