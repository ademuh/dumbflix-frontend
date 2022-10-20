def credential = 'ade-test'
def server = 'ads@103.176.79.216'
def dir ='/home/ads/dumbflix-frontend'

pipeline{
    agent any
    stages{
        stage('Pull test - master'){
            when{
		branch "master"
		}
            steps{
                sshagent([credential]){
                    sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
                    cd ${dir}
                    git config --global user.email muhamaddestar5@gmail.com
                    git config --global user.name ademuh
                    git pull origin master
                    exit
                    EOF"""
                    }
                }
            }
        stage('Pull test - development'){
            when{
                branch "development"
                }
            steps{
                sshagent([credential]){
                    sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
                    cd ${dir}
                    git config --global user.email muhamaddestar5@gmail.com
                    git config --global user.name ademuh
                    git pull origin development
                    exit
                    EOF"""
                    }
                }
            }
        stage('Pull test - production'){
            when{
                branch "production"
                }
            steps{
                sshagent([credential]){
                    sh """ssh -o StrictHostKeyChecking=no ${server} << EOF
                    cd ${dir}
                    git config --global user.email muhamaddestar5@gmail.com
                    git config --global user.name ademuh
                    git pull origin production
                    exit
                    EOF"""
                    }
                }
            }
        }
    }
