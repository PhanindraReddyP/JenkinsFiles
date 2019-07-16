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
				mvn 'clean package'
				echo 'Package Built'
			}
		}
	}
}
