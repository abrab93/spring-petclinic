pipeline {
   agent any
   tools{
       jdk 'openJdk1.8'
       maven 'maven363'
   }
   stages {
      stage('Clone stage') {
         steps {
            git changelog: false, credentialsId: 'abrabGIT', poll: false, url: 'https://github.com/abrab93/spring-petclinic.git'
         }
      }
      stage('Compile stage') {
         steps {
            sh 'mvn clean compile'
         }
      }
      stage('Test stage') {
         steps {
            sh 'mvn test'
         }
      }
   }
}
