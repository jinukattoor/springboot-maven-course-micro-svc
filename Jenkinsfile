pipeline{
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage('checkout the code'){
            steps{
                git url:'https://github.com/jagdishmodi/springboot-maven-course-micro-svc.git', branch: 'master'
            }
        }
        stage('build the code'){
            steps{
                sh 'mvn clean package'
            }
        }
		stage('Docker Build') {
       agent any
       steps {
        sh 'docker build -t jinudock/conimage:TestDockerBuild .'
      }
    }
}
}

