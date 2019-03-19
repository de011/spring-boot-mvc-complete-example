node {
   
   
   checkout scm
   
   stage 'compile parent pom'
   dir("mylab-parent-pom") {
     sh "java -version"
     sh "mvn clean install"
     echo 'Compiled parent pom succesfully'
   }
   
   stage 'run unit test mylab core'
   dir("mylab-core") {
     sh "mvn test"
     echo 'Unit test has passed succesfully'
     stage 'run package mylab core '
     sh "mvn package"
     echo 'App has been packaged succesfully'
   }
   
   stage 'run unit test rest layer'
     dir("spring-boot-mvc-rest") {
     sh "mvn test"
     echo 'Unit test has passed succesfully'
     stage 'run package rest layer'
     sh "mvn package"
     echo 'App has been packaged succesfully'
     stage 'deploy app to develop server'
     input message: 'Do you want to deploy your artifact to develop server?', ok: 'OK', submitter: 'admin'
     echo 'App has been deployed to develop server'
     //TODO DEPLOY TO SERVER XXXXX
    }  
   
}