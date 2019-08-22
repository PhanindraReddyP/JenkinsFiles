pipeline {
	agent any
	stages {
		stage ('Clone') {
			steps {
				git 'https://github.com/PhanindraReddyP/shopizer.git'
				echo 'Repository Cloned!!'
			}
		}
		stage ('Build') {
			steps {
				bash 'mvn clean package'
				echo 'Package Built'
				archiveArtifacts '**/*.jar'
			}
		}
	}
}
