# mvn install command

Although I used `mvn` for long in my daily work, it's the first time I seriously read through the official documentation to get the full descriotion about
it's "install" command.

The below section is from https://maven.apache.org/guides/getting-started/index.html with respect.

```
Now you'll want to install the artifact you've generated (the JAR file) in your local repository (${user.home}/.m2/repository is the default location). For more information on repositories you can refer to our Introduction to Repositories but let's move on to installing our artifact! To do so execute the following command:

mvn install
```

It's crystal clean what `mvn install` does. In practice some big projects are having a lot of modules and to manage the dependencies to its own modules, or from other local built 3rd party projects. An approach is to
install all the stuff into local maven repository and reference them with maven like any external artifacts.

<br />
When looking through the maven "Getting Started" guide, I also find something useful and interesting.

Build only the test code, with 
```$ mvn test-compile```

The patterns `mvn test` collecting test cases
1. \*\*/\*Test.java
2. \*\*/Test\*.java
3. \*\*/\*TestCase.java

And these files are excluded by default.
1. \*\*/Abstract\*Test.java
2. \*\*/Abstract\*TestCase.java

NOTE: I used JUnit annotation "@Ignore" (or something alike?) to exlude the "base" classes of test cases. However the way of maven is much elegant.

A **lesson** to learn: Do spend some time to read the **official guide**. It will pay you back in time.

Tags: java, maven, mvn, unit test
