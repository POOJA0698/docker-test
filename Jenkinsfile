
pipeline {
    agent any
    
    tools {
        maven "maven-3.9.12"
    }

    stages {

        stage('Clone') {
            steps {
                echo "Repo already cloned by Jenkins"
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t 9981536579/test:latest .'
            }
        }

        stage('Docker Push') {
            steps {
                sh 'docker push 9981536579/test:latest'
            }
        }

        stage('K8S Deploy') {
            steps {
                sh 'kubectl apply -f k8s/deployment.yaml'
            }
        }
    }
}
