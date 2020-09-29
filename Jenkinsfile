pipeline {
  agent any
  stages {
    stage('Pull') {
      steps {
<<<<<<< HEAD
        git(url: 'https://github.com/ssrksiva/testpipeline2.git', branch: 'develop', poll: true)
=======
        git(url: 'https://github.com/ssrksiva/testpipeline2.git', branch: 'develop', poll: true, credentialsId: 'testgithub')
>>>>>>> d50eddc868edfeea8e5353b40cc33b9841a4a383
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
<<<<<<< HEAD
	  withCredentials([usernamePassword(credentialsId: env.testgithub, usernameVariable: 'Username', passwordVariable: 'Password')]) {
                    script {
                        env.encodedPass=URLEncoder.encode(PASS, "UTF-8")
                    }
                    sh 'git merge -s ours develop --allow-unrelated-histories'
                   sh 'git push -u origin master'
                } 
        
=======
        sh 'git push origin master'
>>>>>>> d50eddc868edfeea8e5353b40cc33b9841a4a383
      }
    }

  }
}