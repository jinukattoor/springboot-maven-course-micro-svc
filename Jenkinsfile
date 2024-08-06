pipeline{
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage('checkout the code'){
            steps{
                git url:'https://github.com/jinukattoor/springboot-maven-course-micro-svc.git', branch: 'master'
            }
        }
        stage('build the code'){
            steps{
                sh 'mvn clean package'
            }
        }
		stage('Docker Build') {
            steps {
        sh 'docker build -t jinudock/spring-petclinic:latest .'
      }
    }
	 stage('Docker Push') {
		steps {
		withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) 
		{
			sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
			sh 'docker push jinudock/conimage:latest'
		}
	 
	 }
		
}
}
}
