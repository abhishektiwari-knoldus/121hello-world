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
          deploy adapters: [tomcat9(credentialsId: '6f1ca071-d432-4068-8a56-8fb75ec558d3', url: 'http://13.49.134.29:8080/')], contextPath: '', onFailure: false, war: 'target/*.war' 
        }
      }
    }
  }
}
