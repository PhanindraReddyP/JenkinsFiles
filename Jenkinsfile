pipeline {
	agent any
	stages {
		stage ('SCM') {
			step {
				git clone 'https://github.com/PhanindraReddyP/test.git'
			}
		}
		stage ('Build') {
			step {
				sh 'mvn clean package'
			}
		}
	}
}
