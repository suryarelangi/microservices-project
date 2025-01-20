pipeline {
    agent any

    stages {
        stage('Building Image') {
            steps {
                sh "docker build -t suryarelangi/adservice:latest ."
            }
        }
        stage("Pushing image to DockerHub"){
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred') {
                        sh "docker push suryarelangi/adservice:latest"
                    }
                }
            }
        }
    }
}
