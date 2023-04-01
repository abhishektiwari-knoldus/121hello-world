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
          deploy adapters: [tomcat9(credentialsId: '7bb8929b-9f38-466c-8ff0-bfe686a1e64b', url: 'http://3.110.131.141:8081/')], contextPath: '', onFailure: false, war: 'target/*.war' 
        }
      }
    }
  }
  post{
        success{
            mail to: "abhisheksandilya03@gmail.com",
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
