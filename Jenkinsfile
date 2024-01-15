pipeline {
  agent any
  stages {
    stage('Get code') {
      steps {
        git branch: 'IST', credentialsId: '32575326-a981-4fbc-ab10-8867b851b645', url: 'https://github.com/miguelFV/MSSQLSERVER_instance.git'
        bat ("dir")
        echo 'code Downloaded'
      }
    }
    stage('Apply changes') {
      steps {
        script{
          def isSuccess = true
          def projects = null 
          try {
            projects = readJSON file: "apply_sql.json", returnPojo: true
            //echo "si leeyo correcto"
          }catch(e) {
            isSuccess = false
          }
          //print projects
          projects['files_to_apply'].each {
            def sqlToApply = it
            echo "Try to execute "+sqlToApply.toString();
            try {
             bat("SQLCMD -S MIKE-PC -i ${sqlToApply.toString()}")
             echo "EXECUTE SUCCESS FOR "+sqlToApply.toString();
            }catch(e) {
              isSuccess = false
              echo "FAILED TO EXECUTE "+sqlToApply.toString();
            }
          }
        }
        bat("SQLCMD -S MIKE-PC -Q \"select name, database_id from sys.databases\" ")
      }
    }
  }
}