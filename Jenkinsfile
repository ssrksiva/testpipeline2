pipeline {
  agent any
  stages {
    stage('Pull') {
      steps {
        git(url: 'https://github.com/vvishal0812/jhipster6-demo.git', branch: 'master', poll: true)
      }
    }

    stage('Check Java') {
      steps {
        sh 'java -version'
      }
    }

    stage('Clean') {
      steps {
        sh 'chmod +x mvnw'
        sh './mvnw -ntp clean -P-webpack'
      }
    }

    stage('Deliver for development') {
      when {
        branch 'develop'
      }
      steps {
        sh 'git merge -X theirs develop --allow-unrelated-histories'
        sh 'git push origin master'
      }
    }

  }
}