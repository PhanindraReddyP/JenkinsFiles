pipeline {
	agent any
	tools {
        maven 'Maven_3.3.9' 
        }
	stages {
		stage ('Build') {
			steps {
				sh 'mvn clean package'
			}
		}
	}
}
