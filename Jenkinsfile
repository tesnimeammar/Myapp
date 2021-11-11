pipeline {

  agent any

    stages {
        stage('Pull') {
             steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                        userRemoteConfigs: [[
                            credentialsId: '12f47b4d-e39b-4dcf-bf05-515f293f9445',
                            url: 'https://github.com/tesnimeammar/Myapp.git']]])
                }
            }
        }
        
	stage('Install') {
             steps{
                script{
                    sh "sudo npm install"
                }
            }
        }

	stage ('Build') {
	
			steps {
			
			sh "ansible-playbook Ansible/build.yml -i Ansible/inventory/host.yml"
	
			}


	}




	stage('ng Build') {
             steps{
                script{
                    sh "sudo ng build"
                }
            }
        }

	 stage('Docker') {
             steps{
                
                    sh "ansible-playbook Ansible/docker.yml -i -vvv Ansible/inventory/host.yml"
                
            }
        }






	}




}
