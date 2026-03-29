pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                git 'https://github.com/Shyamsandeep28/Devops-project.git'
            }
        }
          stage('test by trivy') {
            steps {
                sh 'trivy repo https://github.com/Shyamsandeep28/Devops-project.git'
            }
        }

   stage('test by sonar') {
            steps {
                sh 'mvn sonar:sonar -Dsonar.host.url=http://172.178.49.66:9000/ -Dsonar.login=sqa_b0de691185abae8cefe67ea337a40ebeff7a457f'
            }
        }
        
        
          stage('build') {
            steps {
               sh 'mvn clean'
              sh 'mvn package'

            }
        }
        
        
          stage('build image') {
            steps {
                sh 'docker build -t newimage .'
            }
        }
        
          stage('testing by Trivy') {
            steps {
                sh 'trivy image newimage'
            }
        }
     stage('deploy') {
            steps {
                sh 'docker rm -f newapplication'
                sh 'docker run -d --name newapplication -p 8089:8080 newimage'
            }
        }

    }
}
