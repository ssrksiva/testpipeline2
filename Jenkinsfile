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
    
	  withCredentials([usernamePassword(credentialsId: 'testgithub', usernameVariable: 'Username', passwordVariable: 'Password')]) {
                    script {
                        env.encodedPass=URLEncoder.encode(PASS, "UTF-8")
                    }
                    sh 'git merge -s ours develop --allow-unrelated-histories'
                   sh 'git push -u origin master'
                } 
      }
    }

  }
}