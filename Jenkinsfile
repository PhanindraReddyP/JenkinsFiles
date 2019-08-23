pipeline {
	agent any
	tools {
		jdk 'JAVA8'
		maven 'maven'
	}
	stages {
		stage ('Clone') {
			steps {
				git 'https://github.com/wakaleo/game-of-life.git'
				echo 'Repository Cloned!!'
			}
		}
		stage ('Build') {
			steps {
				sh 'mvn clean package'
				echo 'Package Built'
				archiveArtifacts '**/*.jar'
			}
		}
	}
}
