pipeline{
    agent any
    stages{
        stage('checkout'){
            steps{
                 git url: 'https://github.com/akshu20791/health-care-project/'
                 echo 'github url checkout'
            }
        }
        stage('codecompile'){
            steps{
                echo 'starting compiling'
                sh 'mvn compile'
            }
        }
        stage('codetesting'){
            steps{
                sh 'mvn test'
            }
        }
        stage('qa check'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('package the code'){
            steps{
                sh 'mvn package'
            }
        }
        stage('run dockerfile'){
          steps{
               sh 'docker build -t myimg1 .'
           }
         }
        stage('port expose'){
            steps{
                sh 'docker run -dt -p 8082:8082 --name c001 myimg1'
            }
        }   
    }
}