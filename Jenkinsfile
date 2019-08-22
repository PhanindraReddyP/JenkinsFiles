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
				tool name: 'MAVEN3.3.9', type: 'maven'
				sh 'maven clean package'
				echo 'Package Built'
				archiveArtifacts '**/*.jar'
			}
		}
	}
}
