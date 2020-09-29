pipeline {
  agent any
  stages {
    stage('Pull') {
      steps {
        git(url: 'https://github.com/ssrksiva/testpipeline2.git', branch: 'develop', poll: true, credentialsId: 'testgithub')
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
        sh 'git push --set-upstream origin master'
      }
    }

  }
}