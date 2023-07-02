pipeline{
    
    agent any
    environment{
        registry = "355064287350.dkr.ecr.us-east-1.amazonaws.com/project-application"
    }
    
    stages {
        
        stage('Checkout'){
            steps{
            checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: '93f87964-92eb-426b-86fa-7b0bee590681', url: 'https://github.com/SwapnilDA-20/application-js.git']]])
            }
        }
        stage('Build'){
            steps{
                sh 'docker build -t nodejs-app .'
                sh 'docker tag nodejs-app 355064287350.dkr.ecr.us-east-1.amazonaws.com/project-application:v1'
                
                script {
                    docker.withRegistry("https://355064287350.dkr.ecr.us-east-1.amazonaws.com", "ecr:us-east-1:credentials") { 
                    docker.image("355064287350.dkr.ecr.us-east-1.amazonaws.com/project-application:v1").push()
                    }
                }
            }
        }
        stage('Deploy to Host Server'){
            steps{
                sshagent(credentials : ['ssh-key']){
                    sh 'ssh -o StrictHostKeyChecking=no ubuntu@10.0.12.217 docker run -itd -p 8080:8081 355064287350.dkr.ecr.us-east-1.amazonaws.com/project-application:v1'                
                }
            }
        }
    }
}
