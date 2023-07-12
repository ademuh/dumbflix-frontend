def branch = "master"
def remote = "origin"
def directory = "~/dumbflix-frontend"
def server = "ads@103.187.146.33"
def cred = "dumbflix"

pipeline{
	agent any
	stages{
		stage('repo pull'){
		     steps{
			sshagent([cred]){
				ssh """ssh -o StrictHostKeyChecking=no ${server} << EOF
				cd ${directory}
				git pull ${remote} ${branch}
				exit
				EOF"""
				}
			}
		}
	}
}
