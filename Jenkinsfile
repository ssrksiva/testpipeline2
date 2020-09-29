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


    stage('Deliver for development') {
      when {
        branch 'develop'
      }
      steps {
        withCredentials(bindings: [usernamePassword(credentialsId: 'testgithub', usernameVariable: 'Username', passwordVariable: 'Password')]) {
          script {
            env.encodedPass=URLEncoder.encode(PASS, "UTF-8")
          }
         sh 'git config --global credential.username {ssrksiva}'
         sh 'git config --global credential.helper "!echo password={14Dec@1991}; echo"'
          sh 'git push -u origin master'
        }

      }
    }

  }
}