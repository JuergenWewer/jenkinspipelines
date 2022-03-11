pipeline{
    agent none
    stages {
        stage('cloneRepo') {
            agent any
            steps {
                git 'https://github.com/JuergenWewer/yuuvis.git'                
            }
        }
        stage('push Repo to deployment Repo') {
            agent any
            steps {
                sh '''git remote set-url origin https://github.com/JuergenWewer/deploymentrepository.git
                git add .
                git commit -m "initial setup"
                git push
                '''
           }
        }
    }
}
