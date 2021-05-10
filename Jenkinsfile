pipeline{
	agent any
	tools {
	    nodejs "NodeJS"
	}
  stages {
      stage('Test') {
          steps {
              echo 'Testing'
              sh 'npm install'
              sh 'npm run test_Failure'
          }
      }
  }
	post{

		always{
			echo 'Finished'
		}
		failure{
				echo 'Failure'
				emailext attachLog: true,
          body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}",
					to: 'eszczupak82@gmail.com',
					subject: "Test failed"
		}
		success{
      echo 'Success'
      emailext attachLog: true,
        body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}",
        to: 'eszczupak82@gmail.com',
        subject: "Test success"
		}
	}
}

