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
          deploy adapters: [tomcat9(credentialsId: '60e75ebd-4e55-47e6-bad1-983bcac4756f', url: 'http://3.110.131.141:8081/')], contextPath: '', onFailure: false, war: 'target/*.war' 
        }
      }
    }
  }
}
