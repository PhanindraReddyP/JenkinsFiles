pipeline {
	agent any
	stages {
		stage ('Build') {
			steps {
				withMaven(version:apache-maven-3.3.9) {
				sh 'mvn clean package'
				}
			}
		}
	}
}
