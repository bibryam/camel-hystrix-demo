#### Camel Hystric component demo on JBoss Fuse 6.2

Install all the prerequisites for hystrix component:

    install -s mvn:org.apache.servicemix.bundles/org.apache.servicemix.bundles.commons-configuration/1.9_2
    install -s mvn:org.apache.servicemix.bundles/org.apache.servicemix.bundles.commons-digester/1.8_4
    install -s mvn:org.apache.commons/commons-jexl/2.1.1
    install -s mvn:org.apache.servicemix.bundles/org.apache.servicemix.bundles.commons-jxpath/1.3_1
    install -s wrap:mvn:com.netflix.archaius/archaius-core/0.4.1
    install -s mvn:org.apache.servicemix.bundles/org.apache.servicemix.bundles.hystrix/1.4.23_1


Install hystrix component by overriding imports so it runs with Camel 2.15 that is shipped in JBoss Fuse 6.2:
  (You can build the camel-hystrix component from Camel master 2.18-SNAPSHOT or clone and build it from [here|https://github.com/bibryam/camel-hystrix])

    install -s 'wrap:mvn:org.apache.camel/camel-hystrix/2.18-SNAPSHOT/$overwrite=merge&Import-Package=com.netflix.hystrix;version="[1.4,2)",com.netflix.hystrix.strategy;version="[1.4,2)",com.netflix.hystrix.strategy.concurrency;version="[1.4,2)",com.netflix.hystrix.strategy.properties;version="[1.4,2)",org.apache.camel;version="[2.15,2.19)",org.apache.camel.impl;version="[2.15,2.19)",org.apache.camel.spi;version="[2.15,2.19)",org.apache.camel.util;version="[2.15,2.19)",org.osgi.framework;version="[1.5,2)",org.osgi.framework.wiring;version="[1.0,2)"'


Build the current demo project and install in JBoss Fuse:

    mvn clean install

    features:install camel-core
    features:install camel-http4
    install -s mvn:com.ofbizian/camel-hystrix-demo/1.0.0
