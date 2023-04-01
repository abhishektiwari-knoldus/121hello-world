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
          deploy adapters: [tomcat9(credentialsId: '548235bc-ab9e-479a-962d-99b77b00d918', url: 'http://13.49.134.29:8080/')], contextPath: '', onFailure: false, war: 'target/*.war' 
        }
      }
    }
  }
  post{
        success{
            mail to: "abhisheksandilya03gmail.com",
            subject: "Build is successfull",
            body: "success"
        }
    failure{
      mail to: "abhisheksandilya03@gmail.com",
            subject: "Build is failed",
            body: "failed"
    }
  }
  
}
