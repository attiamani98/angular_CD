pipeline {
	    agent any
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
	     	
	        stage('npm install'){
	            steps{
	                script{
	                    sh "npm install --force"
	                }
	            }
	        }
	        stage('Build'){
	            steps{
	                script{ 
	                    sh "ansible-playbook Ansible/build.yml -i Ansible/inventory/host.yml"
	                }
	            }
	            }
	              stage('docker'){
            steps{
                script{
                    sh "ansible-playbook Ansible/docker.yml -i Ansible/inventory/host.yml"
                }
            }
        }
       


 }
	            }
