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
      stage("build & SonarQube analysis") {
          steps {
             withSonarQubeEnv('sonarqbScanner') {
               sh 'mvn clean install org.sonarsource.scanner.maven:sonar-maven-plugin:3.3.0.603:sonar org.jacoco:jacoco-maven-plugin:prepare-agent -Dmaven.test.failure.ignore=true -Dsonar.projectKey=petclinic-app'
             }
           }
        }
   }
}
