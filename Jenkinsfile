#!/usr/bin/env groovy

void checkIfPRContainsListView{
	def buildStatus = true;
	def numberOfUnwantedFiles = sh (script: 'find folder1 -maxdepth 1 -type f -name '*.listView' -o -name '.report' | wc -l',returnStdout: true).trim() 
	when{  
		changeRequest()
	}
		if (numberOfUnwantedFiles.toInteger() > 1) {
			currentBuild.result = 'ABORTED'
			error('Build has been stopped, because on ListView in files.')
		}
}

pipeline {
    agent any
        stages {
		stage('Check files'){
		when{  
			changeRequest()
			}
		steps {
			checkIfPRContainsListView()
			}
		}
	}
}
		
