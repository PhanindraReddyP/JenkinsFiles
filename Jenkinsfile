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
			def M2_HOME = tool name: 'MAVEN3.3.9', type: 'maven'
			steps {
				sh '{M2_HOME}/bin/mvn clean package'
				echo 'Package Built'
				archiveArtifacts '**/*.jar'
			}
		}
	}
}
