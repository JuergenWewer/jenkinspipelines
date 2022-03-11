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
                sh '''
                git remote rename origin upstream
                git remote add origin https://github.com/JuergenWewer/deploymentrepository.git
                git push origin main
                '''
           }
        }
    }
    post {
        always {
            deleteDir()
        }
    }
}
