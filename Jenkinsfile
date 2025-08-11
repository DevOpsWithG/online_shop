pipeline {
    agent any
    
    /*tools {
       nodejs "NodeJS24"
    }*/
  
    
    stages {
        stage ("checkout"){
            steps {
                cleanWs()
                git url: "https://github.com/DevOpsWithG/online_shop.git", branch: "Hackathon"
            }
        }
        /*stage ("Code Build"){
            steps {
                sh '''
                npm install 
                npm run build
                '''
                
            }
        }*/
        /*stage ("Static Code Analysis"){
            steps {
                sh '''
                npx eslint --max-warnings 0
                '''
            }
        }*/
        /*stage ("Unit Tests"){
            //There should test script in code to run this stage
            steps {
                sh '''
                npm test -- --coverage  
                '''
                
            }
        }*/
        /*stage ("Security Scan"){
            steps {
                sh '''
                npm audit fix
                npm audit --audit-level=high
                
                '''
                
            }
        }*/
        stage ("Docker Build"){
            steps {
                sh '''
                docker build -t ganesh51/online-shop:latest .
                '''
            }
        }
        /*stage ("Image Scan"){
            steps { 
                sh '''
                trivy image --exit-code 1 --severity HIGH,CRITICAL ganesh51/online-shop:v1.0.$BUILD_NUMBER
                '''
            }
        }*/
        stage ("Docker Push"){
            steps {
                
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh 'echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin'
                    sh 'docker push ganesh51/online-shop:latest'
                }
                
            }
        }
        stage('Deploy to GKE') {
            steps {
                 withCredentials([file(credentialsId: 'gcp-sa-key', variable: 'GOOGLE_APPLICATION_CREDENTIALS')]) {
                     sh '''
                     gcloud auth activate-service-account --key-file=$GOOGLE_APPLICATION_CREDENTIALS
                     gcloud config set project integral-nimbus-461213-u7
                     gcloud container clusters get-credentials autopilot-cluster --region us-central1

                     kubectl apply -f manifest.yaml
                     '''
                 }
            }
        }
        
    }
}
