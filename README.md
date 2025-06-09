# My Portfolio Workspace

This workspace contains various resources, projects, and files related to my academic and professional journey.

## Visit My Portfolio

You can view my portfolio here: [Nandan S Portfolio](https://sites.google.com/view/nandan-s-?usp=sharing)

## Overview

This portfolio showcases my academic achievements, professional skills, and projects. It includes:
- **Projects**: Data science, DevOps, and portfolio-related projects.
- **Technical Skills**: Python, R programming, and NLP.
- **Certifications and Achievements**: Details of certifications and accomplishments.
- **gallery**
- 


## Technologies Used
- Google Sites

## Contact
For any questions, feel free to reach out via my [GitHub Profile]([https://github.com/](https://github.com/Nandannn1817)).

<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">

  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>MyMavenApp</artifactId>
  <version>1.0-SNAPSHOT</version>
  <packaging>jar</packaging>

  <properties>
    <!-- Java version -->
    <maven.compiler.source>17</maven.compiler.source>
    <maven.compiler.target>17</maven.compiler.target>

    <!-- JUnit and Surefire versions -->
    <junit.jupiter.version>5.10.1</junit.jupiter.version>
    <surefire.plugin.version>3.0.0-M7</surefire.plugin.version>
  </properties>

  <dependencies>
    <!-- JUnit 5 API for writing tests -->
    <dependency>
      <groupId>org.junit.jupiter</groupId>
      <artifactId>junit-jupiter-api</artifactId>
      <version>${junit.jupiter.version}</version>
      <scope>test</scope>
    </dependency>

    <!-- JUnit 5 Engine for running tests -->
    <dependency>
      <groupId>org.junit.jupiter</groupId>
      <artifactId>junit-jupiter-engine</artifactId>
      <version>${junit.jupiter.version}</version>
      <scope>test</scope>
    </dependency>
  </dependencies>

  <build>
    <plugins>
      <!-- Compiler plugin for Java 17 -->
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-compiler-plugin</artifactId>
        <version>3.8.1</version>
        <configuration>
          <source>${maven.compiler.source}</source>
          <target>${maven.compiler.target}</target>
        </configuration>
      </plugin>

      <!-- Surefire plugin to run JUnit 5 tests -->
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-surefire-plugin</artifactId>
        <version>${surefire.plugin.version}</version>
        <configuration>
          <argLine>--add-opens java.base/java.lang=ALL-UNNAMED</argLine>
        </configuration>
      </plugin>
    </plugins>
  </build>

</project>


package com.example;

public class App {
    public String getMessage() {
        return "Hello World!";
    }

    public static void main(String[] args) {
        System.out.println(new App().getMessage());
    }
}



package com.example;

import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertEquals;

class AppTest {

    @Test
    void testGetMessage() {
        App app = new App();
        assertEquals("Hello World!", app.getMessage(), "Message should be 'Hello World!'");
    }
}


plugins {
    // Apply the Java plugin for compiling Java code
    id 'java'
    // Apply the application plugin to add support for building an application
    id 'application'
}

group = 'org.example'
version = '1.0'

repositories {
    // Use Maven Central for resolving dependencies.
    mavenCentral()
}

dependencies {
    // Define your dependencies. Use JUnit Jupiter (JUnit 5) for testing.
    testImplementation 'org.junit.jupiter:junit-jupiter-api:5.10.0'
    testRuntimeOnly 'org.junit.jupiter:junit-jupiter-engine:5.10.0'
    // If using parameterized tests
    testImplementation 'org.junit.jupiter:junit-jupiter-params:5.10.0'
}

application {
    // Define the main class for the application.
    mainClass = 'org.example.App'
}

// A custom task example: printing a greeting
task hello {
    doLast {
        println 'Hello, Gradle!'
    }
}


plugins {
    // Apply the Java plugin for compiling Java code
    java
    // Apply the application plugin to add support for building an application
    application
}

group = "org.example"
version = "1.0"

repositories {
    mavenCentral() // Configures Maven Central for dependencies
}

dependencies {
    // Define dependencies using Kotlin DSL syntax. Use JUnit Jupiter (JUnit 5) for testing.
    testImplementation("org.junit.jupiter:junit-jupiter-api:5.10.0")
    testRuntimeOnly("org.junit.jupiter:junit-jupiter-engine:5.10.0")
    // If using parameterized tests
    testImplementation("org.junit.jupiter:junit-jupiter-params:5.10.0")
}

application {
    mainClass.set("org.example.App") // Specifies the main class
}

// A custom task example using Kotlin DSL
tasks.register("hello") {
    doLast {
        println("Hello, Gradle with Kotlin DSL!")
    }
}



pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/devops-ds/your-gradle-project.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh './gradlew clean build'
            }
        }

        stage('Test') {
            steps {
                sh './gradlew test'
            }
        }
    }

    post {
        always {
            junit '**/build/test-results/test/*.xml'
        }
    }
}



pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/devops-ds/your-maven-project.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh '/usr/bin/mvn clean package'
            }
        }

        stage('Test') {
            steps {
                // Tests assumed to run during Build
            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml'
        }
    }
}


---
- name: Basic Server Setup
  hosts: local
  become: yes 
  tasks:
    - name: Update apt cache
      apt:
        update_cache: yes

    - name: Install curl
      apt:
        name: curl
        state: present




