node{

environment {
	//	DOCKERHUB_CREDENTIALS=credentials('dockerhub-cred-sampofi')
         USERNAME = credentials('DOCKER_USERNAME')
         PASSWORD = credentials('DOCKER_PASSWORD')                
	}


    stage('SCM Checkout')
    {
        git credentialsId: 'dcbdfb03-7055-4f98-8e26-077f117c0e5e', url: 'https://github.com/sampox/shoppi.git'
    }
    
    stage('Build') {

		//	steps {
		//		sh 'docker build -t sampofi/phpmysql:latest .'
		//	}
	sh '/usr/local/bin/docker-compose build'
        sh '/usr/local/bin/docker-compose up -d'
		}
    stage('Login') {
	//steps {
		sh 'docker login -u ${USERNAME} -p ${PASSWORD}'
//	}
    }
  stage('Push') {

//			steps {
				sh 'docker push sampofi/phpmysql:latest'
//			}
		}

	post {
		always {
			sh 'docker logout'
		}
	}
}
