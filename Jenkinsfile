pipeline {
  agent any
  stages {
    stage('Get code') {
      steps {
        git ("https://github.com/miguelFV/MSSQLSERVER_instance.git",'IST')
        bat ("dir")
        echo 'code Downloaded'
      }
    }
    stage('Apply changes') {
      steps {
        def isSuccess = true
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
        }
        bat("SQLCMD -S MIKE-PC -Q \"select name, database_id from sys.databases\" ")
      }
    }
  }
}