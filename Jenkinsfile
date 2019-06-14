pipeline {
    agent {
		docker{
			image 'maven:3-alpine'
		}
	}
    stages {
        stage('build') {
            steps {
                sh "mvn clean package"
            }
        }
        stage('test') {
            steps {
                sh "mvn test"
            }
			post{
				always{
					junit 'target/surefire-reports/*.xml'
				}
			}
        }
        stage('deliver') {
            steps {
                sh "./jenkins/scripts/deliver.sh"
            }
        }
    }
}
