---
layout: post
title:  "Make a CEP using Apache Flink."
date:   2017-11-02 12:15:12 -0500

tags:
  - Apache Flink
  - Complex Event Processing
  - CEP
  - Apache
  - Ubuntu
  - Java
  
categories:
  - Frameworks
---

Here you'll learn how to imeplement a Complex Event Processing with Apache Flink.

## Maven

Maven or Apache Maven is a tool to build Java projects.  
Maven addresses two aspects of building software: first, it describes how software is built, and second, it describes its dependencies.  
* Install apache-maven:

      wget www-eu.apache.org/dist/maven/maven-3/3.5.2/binaries/apache-maven-3.5.2-bin.zip

* Unzip the file and cp to `/opt/` directory.

      sudo cp -r apache-maven-3.5.2/ /opt/

* Next, modify `.profile` file:

      export PATH=/opt/apache-maven-3.5.2/bin:$PATH

## Apache Flink

Apache Flink is an Open Source Stream Processing Framework written in Java and Scala.  
* First, create a directory `Apache/Flink`.

* Then, goes to `Apache/Flink` and download apache-flink:

      wget https://archive.apache.org/dist/flink/flink-1.3.0/flink-1.3.0-bin-hadoop2-scala_2.10.tgz

* Unzip and start the Flink service:

      ./flink-1.3.0/bin/start-local.sh

## Running an example

NC means OpenBSD netcat, is a package to make connections.

* First, set up a listener port:

      nc -l 9000

* Then, run an example:

      ./flink-1.3.0/bin/flink run flink-1.3.0/examples/streaming/SocketWindowWordCount.jar --port 9000

## Create a project

* Run this script:

      curl https://flink.apache.org/q/quickstart.sh >> createProject.sh

* Then, modify these lines in `createProject.sh`:

      PACKAGE=$1
      -DgroupId=$PACKAGE					                  \
      -DartifactId=$PACKAGE								          \
      -Dpackage=$PACKAGE					                  \

* And, run:

      bash createProject.sh exampleFlink

  You can get my bash pressing [here]()

* Once created, compile and generate `.jar` files running 1 of these commands on root example dir:
 
      mvn clean install -Pbuild-jar
      mvn clean package

* Finally, run this line in the root path of `Apache/Flink`:

      ./flink-1.3.0/bin/flink run -c exampleFlink.WordCount exampleFlink/target/exampleFlink-0.1.jar

## Creating a Complex Event Processing

CEP (Complex Event Processing) is 

* First, add this text on `pom.xml`

      <dependency>
        <groupId>org.apache.flink</groupId>
        <artifactId>flink-cep_2.10</artifactId>
        <version>1.3.2</version>
      </dependency>


