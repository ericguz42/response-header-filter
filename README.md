# Response Header Filter for Tomcat
Add custom headers easily to your Tomcat response using param-name and param-value tags in web.xml

## Installation
* Download latest release (.jar file)
* Put `response-header-filter.jar` in your `$CATALINA_HOME/lib` directory
* Edit your `web.xml` located in `$CATALINA_HOME/conf`
* Add the following filter and filter mapping inside `<web-app>` tag:
    ```xml
    <filter>
        <filter-name>ResponseHeaderFilter</filter-name>
        <filter-class>pl.hordyjewiczmichal.ResponseHeaderFilter</filter-class>
        <init-param>
            <param-name>Your-Header-1</param-name> <!-- put your any header name -->
            <param-value>
                your value1
                your value2
                your value3
            </param-value> <!-- put your header value(s) separated by a new line  -->
        </init-param>
        <init-param>
            <param-name>Your-Header-2</param-name>
            <param-value>some other value</param-value>
        </init-param>
    </filter>
    <filter-mapping>
        <filter-name>ResponseHeaderFilter</filter-name>
        <url-pattern>/*</url-pattern> <!-- choose where header will be added -->
    </filter-mapping>
    ```
In `<init-param>` use `<param-name>` tag to add your custom header and below use `<param-value>` to add value to your header.
You can use multiple values for your header in `<param-value>` - just separate them by a new line.

## Build
* Did the build on Rocky Linux 8 with `Apache Maven 3.5.4 (Red Hat 3.5.4-5)` and OpenJDK `Java version: 17.0.11, vendor: Red Hat, Inc.`
* Set JAVA_HOME `export JAVA_HOME=/usr/lib/jvm/java-17-openjdk`
* Ran the build command `mvn package`

Caveat: I'm a total amateur and did what I'm sure is the bear minimum to get this to do what I needed it to do.
