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
                git config --global user.email "juergen.wewer@gmail.com"
                git config --global user.name "jenkins"
                git remote rename origin upstream
                git remote add origin https://github.com/JuergenWewer/deploymentrepository.git
                git add .
                '''
                withCredentials([gitUsernamePassword(credentialsId: 'gitJWId', gitToolName: 'Default')]) {
                   sh '''
                   git push origin HEAD:main
                   '''
                }
           }
        }
    }
    post {
        always {
            deleteDir()
        }
    }
}
