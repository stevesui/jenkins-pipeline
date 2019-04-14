pipeline {
    agent any
    stages {
        stage('Build Stage') {
            steps {
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                    uname -a
                '''
            }
        }
        stage('Post Build Notification') {
            steps {
                emailext body: 'Build Done.', subject: 'Jenkins Build Successfully', to: 'stevesui@yahoo.com'
            }
        }
    }
}

