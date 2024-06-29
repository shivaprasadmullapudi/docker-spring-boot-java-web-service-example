pipeline {
    agent any
    tools{
        jdk 'OpenJDK8'
        maven 'Maven3'
    }

    stages {
        stage('SCM') {
            steps {
                git changelog: false, poll: false, url: 'https://github.com/shivaprasadmullapudi/docker-spring-boot-java-web-service-example.git'
            }
        }
        stage('Maven Build') {
            steps {
                sh "mvn clean install"
            }
        }
        stage('Docker build & Push') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'jenkins-token') {
                        sh "docker build -t shivaprasadmullapudi359/dockerrepo:tag126 ."
                        sh "docker push shivaprasadmullapudi359/dockerrepo:tag126"
   
                   }
                }
            }
        }
    }
}
