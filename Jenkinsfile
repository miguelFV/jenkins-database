pipeline {
  agent any
  stages {
    stage('query') {
      steps {
        echo 'hello world'
      }
    }
    stage('query2') {
      steps {
        echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
      }
    }
    stage('query2') {
      steps {
        bat("SQLCMD -S MIKE-PC \n select name, database_id from sys.databases; go \n")
      }
    }
  }
}