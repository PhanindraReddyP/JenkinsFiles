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
						nexusArtifactUploader(
							nexusVersion: NEXUS_VERSION,
							protocol: NEXUS_PROTOCOL,
							nexusUrl: NEXUS_URL,
							groupId: "gameoflife",
							version: "1.0",
							repository: NEXUS_REPOSITORY,
							credentials: NEXUS_CREDENTIAL_ID,
							artifacts: [
									[artifactId: pom.artifactId,
									classifier: '',
									file: artifactPath,
									type: pom.packaging]
							]
						);
					}
					else {
					error "*** File: ${artifactPath}, could not be found ***";
					}
				}
			}
		}
	}
}
