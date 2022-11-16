pipeline {
	    agent any
	    tools {nodejs "nodejs"}
	      
	    stages {
	        stage ("Pull") {
	            steps{
	                script{
	                    checkout([$class: 'GitSCM', branches: [[name: '*/main']],
	                    userRemoteConfigs:[[
	                        credentialsId: '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', 
	                           url: 'https://github.com/attiamani98/angular_CD']]])
	                }
	            }
	        }
	      
	
	        
	        stage('Build'){
	            steps{
	                script{ 
	                    sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml 
	                }
	            }
	            }
	              stage('docker'){
            steps{
                script{
                    sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml"
                }
            }
        }
        


 }
	            }


