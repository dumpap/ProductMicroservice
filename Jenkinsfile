pipeline {
    agent { label 'dotnetcore	' }

    stages {
        stage('Pre Build') {
            steps {
                echo 'Starting the Product Service Microservice build'
            }
        }
		stage('Delete Workspace before build starts') {
            steps {
                cleanWs()
            }
        }
        stage('Pull code from GIT') {
            steps {
                git credentialsId: '56cbec1d-59dc-4500-b921-6a2a4958471c', url: 'https://github.com/dumpap/ProductMicroservice.git'
            }
        }
	stage('Restore Packages'){
		steps {
			sh "dotnet restore ProductMicroservice.sln"
		      }
		}
        stage('Publish') {
            steps {
                sh "dotnet publish ProductMicroservice.sln --configuration release"
            }
        }
    }
}
