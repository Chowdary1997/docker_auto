pipeline {
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage('Build Maven'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: '41c5035d-0ded-4a42-94cd-2ae2bf76bf0d', url: 'https://github.com/Chowdary1997/docker_auto.git']]])
                sh 'mvn clean install'
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t javatechie/devops-integration .'
                }
            }
        }
        stage('Push image to Hub'){
            steps{
                script{
                   withCredentials([string(credentialsId: '25cb40a6-1420-4a0e-98ee-d1c36b4a9b37', variable: 'secret text')]) {
                   sh 'docker login -u rajendra.daggubati1997@gmail.com -p ${secret text}'

}
                   sh 'docker push javatechie/devops-integration'
                }
            }
        }
        
    }
}