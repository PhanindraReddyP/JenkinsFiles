pipeline {
	agent any
	tools {
		jdk 'JAVA8'
		maven 'maven'
	}
	environment {
		NEXUS_VERSION = "nexus3"
		NEXUS_PROTOCOL = "http"
		NEXUS_URL = "localhost:8081"
		NEXUS_REPOSITORY = "gameoflife-repo"
		NEXUS_CREDENTIAL_ID = "nexus_credentials"
		
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
