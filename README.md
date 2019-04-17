# AddCertificateInJava1
Add cert:

..\jdk1.8.0_102\bin>keytool -importcert -file "..\cert.crt"  -alias cert_alias

-keystore "..\security\cacerts" -storepass changeit

Maven file:

<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId></groupId>
    <artifactId> </artifactId>
    <version>0.1.0</version>
    <packaging>war</packaging>

    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.1.3.RELEASE</version>
        <!-- <version>1.5.9.RELEASE</version>-->
    </parent>
    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
        <java.version>1.8</java.version>
        <axis2.version>1.7.9</axis2.version>
        <log4j.version>1.2.16</log4j.version>
    </properties>
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter</artifactId>
        </dependency>

        <!-- https://mvnrepository.com/artifact/org.springframework.data/spring-data-jpa -->
        <dependency>
            <groupId>org.springframework.data</groupId>
            <artifactId>spring-data-jpa</artifactId>
            <version>2.1.3.RELEASE</version>
        </dependency>

        <dependency>
            <groupId>org.hibernate</groupId>
           <artifactId>hibernate-core</artifactId>
            <version>5.4.1.Final</version>
            <!--  <version>5.2.9.Final</version>-->
        </dependency>

        <!--<dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-jpa</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.data</groupId>
            <artifactId>spring-data-jpa</artifactId>
            &lt;!&ndash;<version>2.0.1.RELEASE</version>
            <scope>compile</scope>&ndash;&gt;
        </dependency>-->

        <dependency>
            <groupId>org.apache.axis2</groupId>
            <artifactId>axis2-kernel</artifactId>
            <version>${axis2.version}</version>
        </dependency>
        <dependency>
            <groupId>org.apache.axis2</groupId>
            <artifactId>axis2-adb</artifactId>
            <version>${axis2.version}</version>
        </dependency>
        <dependency>
            <groupId>org.apache.axis2</groupId>
            <artifactId>axis2-transport-http</artifactId>
            <version>${axis2.version}</version>
        </dependency>
        <dependency>
            <groupId>org.apache.axis2</groupId>
            <artifactId>axis2-transport-local</artifactId>
            <version>${axis2.version}</version>
        </dependency>
        <dependency>
            <groupId>org.apache.axis2</groupId>
            <artifactId>axis2-xmlbeans</artifactId>
            <version>${axis2.version}</version>
        </dependency>
        <!--<dependency>-->
        <!--<groupId>log4j</groupId>-->
        <!--<artifactId>log4j</artifactId>-->
        <!--<version>1.2.16</version>-->
        <!--</dependency>-->
        <!-- https://mvnrepository.com/artifact/commons-httpclient/commons-httpclient -->
        <dependency>
            <groupId>commons-httpclient</groupId>
            <artifactId>commons-httpclient</artifactId>
            <version>3.1</version>
        </dependency>

        <dependency>
            <groupId>log4j</groupId>
            <artifactId>log4j</artifactId>
            <version>1.2.17</version>
        </dependency>
        <dependency>
            <groupId>com.google.code.gson</groupId>
            <artifactId>gson</artifactId>
            <version>2.2.4</version>
        </dependency>
    </dependencies>

    <build>
        <resources>
            <resource>
                <directory>src/main/resources</directory>
                <filtering>true</filtering>
            </resource>
        </resources>
        <plugins>
            <plugin>
                <groupId>org.apache.axis2</groupId>
                <artifactId>axis2-wsdl2code-maven-plugin</artifactId>
                <version>1.6.2</version>
                <executions>
                    <execution>
                        <goals>
                            <goal>wsdl2code</goal>
                        </goals>
                        <configuration>
                            <wsdlFile>src/main/resources/yaghutwsdl/YaghoutWrapperSrv.wsdl</wsdlFile>
                            <databindingName>adb</databindingName>
                            <packageName>com.prdz.tamakon.yaghutservice</packageName>
                            <outputDirectory>src/main/java</outputDirectory>
                            <flattenFiles>true</flattenFiles>
                            <unpackClasses>true</unpackClasses>
                        </configuration>
                    </execution>
                </executions>
            </plugin>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
            </plugin>
        </plugins>
    </build> 
</project>
