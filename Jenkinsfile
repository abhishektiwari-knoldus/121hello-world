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
          deploy adapters: [tomcat7(credentialsId: 'c7ea6804-7dc4-47be-a419-5cd5d1201407', url: 'http://3.110.131.141:8081/')], contextPath: '', onFailure: false, war: 'target/*.war' 
        }
      }
    }
  }
  post{
        success{
            mail to: "ska78657@gmail.com",
            subject: "Build is successfull",
            body: "success"
        }
    failure{
      mail to: "ska78657@gmail.com",
            subject: "Build is failed",
            body: "failed"
    }
  }
}
