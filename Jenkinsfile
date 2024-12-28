pipeline{
    agent any
    stages{
        stage('checkout the code from github'){
            steps{
                 git url: 'https://github.com/yomeshbarod/health-care-project/'
                 echo 'github url checkout'
            }
        }
        stage('codecompile with yomesh'){
            steps{
                echo 'starting compiling'
                sh 'mvn compile'
            }
        }
        stage('codetesting with yomesh'){
            steps{
                sh 'mvn test'
            }
        }
        stage('qa with yomesh'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('package with yomesh'){
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
