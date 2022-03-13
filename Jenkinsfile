pipeline{
    agent any
    stages {
        stage('push Repo to deployment Repo') {
            agent any
            steps {
                deleteDir()
                sh '''
                git clone 'https://github.com/JuergenWewer/yuuvis.git'
                git config --global user.email "juergen.wewer@gmail.com"
                git config --global user.name "jenkins"
                cd yuuvis
                git remote rename origin upstream
                git remote add origin https://github.com/JuergenWewer/deploymentrepository.git
                git add .
                git commit -m "initial commit"
                ls -al
                pwd
                '''
                withCredentials([gitUsernamePassword(credentialsId: 'gitJWId', gitToolName: 'Default')]) {
                   sh '''
                   git push -f origin HEAD:main
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
