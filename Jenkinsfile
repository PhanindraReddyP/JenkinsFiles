pipeline {
	agent any
	stages {
		stage ('Clone') {
			steps {
				git 'https://github.com/PhanindraReddyP/test.git'
				echo 'Repository Cloned!!'
			}
		}
		stage ('Build') {
			steps {
				maven 'mvn clean package'
				echo 'Package Built'
			}
		}
	}
}
