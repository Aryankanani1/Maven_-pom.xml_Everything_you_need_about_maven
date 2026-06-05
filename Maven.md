Maven

What is Maven?

So Maven is a build automation tool primarily used for Java projects.

It helps to finish the following tasks:

-> Dependency management
-> Project build life cycle
-> Compilation of Source code
-> Deploying to a repository

Now let's move to **pom.xml** file

pom.xml stands for the Project Object Model

which helps to manage build, reporting and documentation

Structure:

<Project>

1. Project Identity
   <groupId></groupId> // your company domain name but in the reversed order com."company-name"
   <artifactId></artifactId> // your project name
   <version></version> // your project version
   <packaging>jar<packaging> / output of your project jar,war etc..

2. properties
   <properties>
   <java.version>21</java.version> java version to use
   <spring.version>3.2.0</spring.version> Reusable variable => ${java.version}
   </properties>

3. repositories  
   // think like an app store where many tools, games are available for your need just download, play and enjoy same as for the project your projects need a library maven goes to repository and downloads it.

there are 3 location types of Repositories

1. local -> in your machine
2. central -> internet (maven central website name)
3. remote -> company/custom server
   <repositories>

  <repository>
     <id>central</id>
        <name>maven central repository</name>
        <url> https://repo.maven.apache.org/maven2 </url> // where it download

    <releases>  // allow stable versions
            <enable>true</enable>
    </releases>

    <snapshots> // blocks unstable version
        <enable>false</enable>
    </snapshots>

  </repository>

</repositories> 
4. dependency
// what is dependency
so dependency is nothing but just a collection of libraries, and classes that are compressed in a small package so it can be used by everyone and this dependency store in the repository.

<dependencies>

    <dependency>
        <groupId>org.springframework.boot</groupId> // who made it company name
        <artifactId>spring-boot-starter-web</artifactId> // library name
        <version>1.0.0<version>
        <scope>compile</scope>
         4 types of scope
         1. compile -> default
         2.test -> only for the testing
         3.provided -> Server provides it
         4.runtime -> only need at a runtime
    </dependency>

</dependencies>

</Project>

maven life cycle
 there are three type of life cycle

1. Default lifecycle
2. Clean lifecycle
3. Site lifecycle


1. default life cycle
 
 validate -> compile -> test -> package -> verify -> install -> deploy

2. Clean lifecycle
    // delete the target folder where all the .class file are there, JARs, WARs, etc.
    pre-clean -> clean -> post-clean
    
3.  site lifecycle  // for the project documentation
    

    // javadoc
    // Dependency list
    // plugin info
    // Custom reports you configure in pom.xml 
    pre-site -> site -> post-site -> site-deploy