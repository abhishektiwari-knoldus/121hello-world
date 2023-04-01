pipeline {
  agent any
  tools {
    maven '3.6.3' 
  }
  stages {
    stage ('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage ('Deploy') {
      steps {
        script {
          deploy adapters: [tomcat 8.5(credentialsId: '4d483032-7e8c-49a6-9eb3-8e245f4b6173', url: 'http://13.49.134.29:8080/')], contextPath: '', onFailure: false, war: 'target/*.war' 
        }
      }
    }
  }
}
