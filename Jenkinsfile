pipeline{
    agent any
    environment{
        DOCKER_IMAGE = 'samag9/fms-dotnet-app'
        DB_HOST = ''
        DB_PORT = '3306'
        DB_NAME = 'fleetdb'
        DB_USER = 'fleetuser'
        DB_PASSWORD = 'fleetpassword'

    }
    stages{
    stage('Clone Repository'){
        steps{
        git url: "https://github.com/Samag1309D/Fleetsystemkins.git", branch:'master'
    }}
    stage('Build docker image'){
        steps{
            sh 'docker build -t $DOCKER_IMAGE .'
        }
    }
    stage('Log in to docker hub'){
        steps{
            withDockerRegistry([credentialsId: 'Samag9',url:'https://index.dockr.io/v1']){
                sh 'echo "logged into docker hub successfully"'
            }
        }
    }
     stage('Push Image to docker hub'){
        steps{
            withDockerRegistry([credentialsId: 'Samag9',url:'https://index.dockr.io/v1']){
                sh 'docker push $DOCKER_IMAGE'
            }
        }
    }
    }
}