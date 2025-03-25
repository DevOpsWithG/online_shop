pipeline{
    agent any;
    
    stages{
        stage('checkout'){
            steps{
                echo "git clone"
                git url:"https://github.com/DevOpsWithG/online_shop.git", branch:"Hackathon"
            }
        }
        stage('Build'){
            steps{
                echo "build code"
                //sh " docker build -t online-shop-${BUILD_NUMBER} ."
            }
        }
        stage('test'){
            steps{
                echo "test code"
            }
        }
        stage('Push'){
            steps{
                echo "Push image"
                withCredentials([usernamePassword(
                    credentialsId: "dockerhub-creds", 
                    passwordVariable: "dockerhubPass", 
                    usernameVariable: "dockerhubUser")]){
                    
                    sh "docker login -u ${env.dockerhubUser} -p ${env.dockerhubPass}"
                    sh "docker images"
                    // sh "docker tag"
                    //sh "docker push"
                }
            }
        }
        stage('Deploy'){
            steps{
                echo "deploy code"
            }
        }
        
        
    }
}
