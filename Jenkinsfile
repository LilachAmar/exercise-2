pipeline {
  agent any
  stages {
    stage('SCM') {
      steps {
        echo 'scm'
      }
    }

    stage('build') {
      parallel {
        stage('proxy') {
          steps {
            sh 'docker compose up -d'
          }
        }

        stage('db') {
          steps {
            sh 'echo \'db...\''
          }
        }

      }
    }   

    stage('test ps') {
      steps {
        sh 'docker compose ps'
        sh 'curl http://localhost:80'
      }
    }
    
    stage('clean') {
      steps {
        sh 'docker compose down'
      }
    }

  }
}
