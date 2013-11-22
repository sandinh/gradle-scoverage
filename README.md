[![Build Status](https://travis-ci.org/SCCT/gradle-scct.png?branch=master)](https://travis-ci.org/SCCT/gradle-scct)

gradle-scct
===========
A plugin to enable the use of SCCT in a gradle Scala project.

This has now been deployed to maven central.

Getting started
---------------
```groovy
buildscript {
    repositories {
        mavenCentral()
        maven { url 'http://mtkopone.github.com/scct/maven-repo' }
    }
    dependencies {
        classpath 'com.sqality:gradle-scct:0.3'
    }
}

apply plugin: 'scct'

dependencies {
    scct 'com.github.scct:scct_2.10:0.2.1'
    compile 'org.scala-lang:scala-library:2.10.1'
}
```

This creates an additional task testCoverage which will run tests against instrumented code

- [x] instrumenting main scala code
- [x] running JUnit tests against instrumented scala code
- [x] failing the build on lack of coverage

Then launch command :
`gradle testScct` or `gradle checkScct` 


CheckScct
---------

By default, when you launch `gradle checkScct` build fail if only 75% of project is covered by tests.

To configure it as you want, add this configuration :
```
checkScct {
    minimumLineRate = 0.5
}
```
