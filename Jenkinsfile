node{

environment {
	//	DOCKERHUB_CREDENTIAL=credentials('dockerhub-cred-sampofi')                
		withCredentials([string(credentialsId: 'dockerhub-cred-sampofi', variable: 'SECRET')])	
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
//		sh 'echo $DOCKERHUB_CREDENTIAL_PSW | docker login -u $DOCKERHUB_CREDENTIAL_USR --password-stdin'
//	}
		
    }
  stage('Push') {

//			steps {
				sh 'docker push sampofi/shoppi'
//			}
		}

	post {
		always {
			sh 'docker logout'
		}
	}
}
