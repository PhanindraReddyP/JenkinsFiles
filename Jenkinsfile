pipeline {
	agent any
	stages {
		stage ('SCM') {
			steps {
				git clone https://github.com/PhanindraReddyP/test.git
			}
		}
		stage ('Build') {
			steps {
				sh 'mvn clean package'
			}
		}
	}
}
