pipeline {
	agent any
	tools {
		jdk 'JAVA8'
		maven 'maven'
	}
	environment {
		NEXUS_VERSION = "nexus3"
		NEXUS_PROTOCOL = "http"
		NEXUS_URL = "192.168.43.199:8081"
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
				sh 'mvn clean package -DskipTests'
				echo 'Package Built'
				archiveArtifacts '**/*.war'
			}
		}
		stage ('publish to Nexus') {
			steps {
				script {
					pom = readMavenPom file: "pom.xml";
					filesByGlob = findFiles(glob: "**/*.war");
					echo "${filesByGlob[0].name} ${filesByGlob[0].path}"
					artifactPath = filesByGlob[0].path;
					artifactExists = fileExists artifactPath;
					if(artifactExists) {
						echo "*** File: ${artifactPath} ***"
						nexusArtifactUploader artifacts: [[artifactId: 'gameoflife', classifier: '', file: '/var/lib/jenkins/workspace/game-of-life/gameoflife-web/target/gameoflife.war', type: 'war']], 
							credentialsId: NEXUS_CREDENTIAL_ID, 
							groupId: 'com.gameoflife', 
							nexusUrl: NEXUS_URL, 
							nexusVersion: NEXUS_VERSION, 
							protocol: NEXUS_PROTOCOL, 
							repository: NEXUS_REPOSITORY, 
							version: '2.0'
					}
					else {
					error "*** File: ${artifactPath}, could not be found ***";
					}
				}
			}
		}
		stage ('deploy to tomcat') {
				steps {
					script {
						sh 'curl http://192.168.0.109:8081/repository/gameoflife-repo/com/gameoflife/gameoflife/2.0/gameoflife-2.0.war -o /usr/share/tomcat/webapps/'
					}
				}
		}
	}
}
