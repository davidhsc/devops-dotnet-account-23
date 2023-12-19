pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                git branch: 'main', url:'https://github.com/davidhsc/devops-dotnet-account-23.git'
            }
        }
        stage('DOCKER BUILD') {
            steps {
               bat(script: 'docker build -t davidhsc/devops-ms-account . ' , returnStdout:true);
               
            }
        }
        stage('DOCKER PUSH') {
            steps {
               bat(script: 'docker login --username davidhsc --password Neca0408Docker ' , returnStdout:true);
               
               bat(script: 'docker push davidhsc/devops-ms-account ' , returnStdout:true);
               
            }
        }
        stage('AZURE CONTAINER INSTANCE') {
            steps {
               bat(script: 'az login --service-principal --username aa424892-e8d3-40a1-8ddd-a967b9664eeb --password QbZ8Q~T5aA8jC5XaGVPlvwMDtVsBw6L-gRYqba7j --tenant b3761ae1-c9a2-4151-9260-ac0345c5e721 ' , returnStdout:true);
               
               bat(script: 'az account set --subscription 76208e3d-a68f-4a97-b2c5-9a9ef10339b9 ' , returnStdout:true);
               
               bat(script: 'az container restart --name msaccount --resource-group Devops ' , returnStdout:true);
               
            }
        }
        
    }
}
