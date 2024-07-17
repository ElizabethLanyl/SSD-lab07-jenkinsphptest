pipeline {
	agent any
    stages {
        stage('Checkout SCM') {
            steps {
                git url: 'https://github.com/ElizabethLanyl/SSD-lab07-jenkinsphptest.git', branch: 'main', credentialsId: 'jenkins-PAT'
            }
        }
		stage('Build') {
			steps {
				bat 'composer install'
			}
		}
		stage('Test') {
			steps {
                bat 'vendor\\bin\\phpunit --log-junit logs\\unitreport.xml -c tests\\phpunit.xml tests'
            }
		}
	}
	post {
	    always{
	        junit testResults: 'logs/unitreport.xml'

	    }
	}
}