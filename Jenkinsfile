pipeline {
  agent any
  stages {
    stage('Get Code 1') {
      steps{
        git credentialsId: '32575326-a981-4fbc-ab10-8867b851b645',
        url: "https://github.com/miguelFV/MSSQLSERVER_instance.git" , branch : "IST"
      }
    }
    stage('Get code') {
      steps {
        bat ("dir")
        echo 'code Downloaded'
      }
    }
    stage('Apply changes') {
      steps {
        /*def isSuccess = true
        def projects = null 
        try {
        projects = readJSON file: "/MSSQLSERVER_instance/apply_sql.json"
        }catch(e) {
        isSuccess = false
        }
        projects.files_to_apply.each {
          def sqlToApply = it
          echo $sqlToApply
          echo sqlToApply
        }*/
        bat("SQLCMD -S MIKE-PC -Q \"select name, database_id from sys.databases\" ")
      }
    }
  }
}