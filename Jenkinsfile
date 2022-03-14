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
                '''
                withCredentials([gitUsernamePassword(credentialsId: 'gitJWId', gitToolName: 'Default')]) {
                   sh '''
                   cd yuuvis
                   pwd
                   ls
                   git remote add upstream https://github.com/JuergenWewer/deploymentrepository.git
                   git push upstream master
                   git status
                   git show-ref
                   git checkout upstream/main
                   git merge -X theirs upstream/master --allow-unrelated-histories --no-edit
                   git push upstream HEAD:main
                   git push --delete upstream master
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
