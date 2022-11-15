pipeline {
	    agent any
	    stages {
	        stage ("Pull") {
	            steps{
	                script{
	                    checkout([$class: 'GitSCM', branches: [[name: '*/master']],
	                    userRemoteConfigs:[[
	                        credentialsId: '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', 
	                           url: 'https://github.com/attiamani98/angular_CD']]])
	                }
	            }
	        }
	        stage('npm install'){
	            steps{
	                script{
	                    sh "npm install --force"
	                }
	            }
	        }
	
	        stage('python test'){
	            steps{
	                script{
	                    sh "python3 --version"
	                }
	            }
	        }
	        stage('Build'){
	            steps{
	                script{ 
	                    sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml -e ansible_become_password=m3m4m5m6"
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


