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
        

	stage ('Build') {
	
			steps {
			
			sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"
	
			}


	}







	}




}
