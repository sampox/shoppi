node{

environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub-cred-sampofi')
	}

    stage('SCM Checkout')
    {
        git credentialsId: 'dcbdfb03-7055-4f98-8e26-077f117c0e5e', url: 'https://github.com/sampox/shoppi.git'
    }
    
    stage('Run Docker Compose File')
    {
        sh 'sudo docker-compose build'
        sh 'sudo docker-compose up -d'
    }
  stage('Login') {
	steps {
		sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
	}
    }
  stage('Push') {

			steps {
				sh 'docker push sampofi/phpmysql:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}
}
