Multi-Module Maven

// it is used for multiple parts of your project

in the main module there is pom.xml file 

now each module has its own pom.xml file
so the dependency is managed by the <dependencyManagement>

in the parent pom.xml file there are two tags
<modules> </modules>
<dependencyManagement> </dependencyManagement>


<project>

<modules>

<module>child-1</module>
<module>child-2</module>
<module>child-3</module>

</modules>

<dependencyManagement> 

   <dependencies>

        <dependency>
        // your dependency will be used by the child pom.xml as well
        </dependency>

   </dependencies>

</dependencyManagement>



</project>


what is the different between <dependencyManagement> and <dependencies>

1. when you define the dependency inside the <dependencyManagement> then you will specify the <version> and <scope> only one time (in short it will help to generalize SCOPE AND VERSION for child modules as well).

the big app split into the smaller chunks 

Single Module          Multi Module
─────────────          ─────────────
one big project   →    parent
                           ├── module-1 (database)
                           ├── module-2 (api)
                           ├── module-3 (web)
                           └── module-4 (common)

example ecommerce app

my-ecommerce/                    ← PARENT
│
├── pom.xml                      ← Parent POM
│
├── ecommerce-common/            ← MODULE 1 (shared code)
│   ├── pom.xml
│   └── src/
│
├── ecommerce-database/          ← MODULE 2 (db layer)
│   ├── pom.xml
│   └── src/
│
├── ecommerce-api/               ← MODULE 3 (REST APIs)
│   ├── pom.xml
│   └── src/
│
└── ecommerce-web/               ← MODULE 4 (frontend/UI)
    ├── pom.xml
    └── src/


Now what is Maven Wrapper?

a portable maven inside of your project
so anyone who accesses the project does not have to install Maven

Without Wrapper          With Wrapper
────────────────         ────────────────
Everyone needs           Maven is INSIDE
Maven installed    →     the project
on their computer        No installation needed


Developer A → has Maven 3.8.0  ❌
Developer B → has Maven 3.9.0  ❌
Developer C → no Maven         ❌

All 3 get different results!

With Maven Wrapper →
Everyone uses Maven 3.9.16  
Same result every time!     

example 

my-project/
│
├── mvnw              ← Wrapper for Mac/Linux
├── mvnw.cmd          ← Wrapper for Windows
│
└── .mvn/
    └── wrapper/
        └── maven-wrapper.properties   ← Maven version config