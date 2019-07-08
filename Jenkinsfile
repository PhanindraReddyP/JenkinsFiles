pipeline {
	agent any
	stages {
		stage ('Build') {
			steps {
				withMaven (maven: 'maven-3.3.9') {
				sh 'mvn clean package'
				}
			}
		}
	}
}
