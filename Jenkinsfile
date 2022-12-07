def branch = "master"
def remote = "origin"
def directory = "~/dumbflix-frontend"
def server = "ads@103.13.206.100"
def cred = "appserver"

pipeline {
	agent any

	stages {
		stage('Repository Pull'){
			steps{
				sshagent([cred]){
				sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
				cd ${directory}
				git pull ${remote} ${branch}
				exit
				EOF"""
				}

			}

		}
		stage('Build Image'){
			steps{
				sshagent([cred]){
				sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
				cd ${directory}
				docker build -t dumbflix-fe .
				exit
				EOF"""
				}
			}
		}
		stage('Run Image'){
			steps{
				sshagent([cred]){
				sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
				docker run -d -p 3000:3000 --name="app-fe" --tty dumbflix-fe
				exit
				EOF"""
				}
			}
		}

	}
}
