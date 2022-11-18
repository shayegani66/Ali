pipeline {
  agent any
  tools {
  maven 'Maven_home'
}
  stages {
    stage ('Build') {
      steps {
        sh 'mvn clean install'
      }
    }
    stage ('Deploy') {
      steps {
        script {
          deploy adapters: [tomcat8(credentialsId: 'java-tomcat', path: '', url: 'http://ec2-18-234-105-235.compute-1.amazonaws.com:8080')], contextPath: null, war: '**/*.war' 
        }
      }
    }
  }
}
