pipeline {
    agent any
    tools {
         maven 'maven_3.6.0'
    }
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
         stage(' Build Subproject and Running Test') {
            steps {
                sh 'echo "About to build jenkins-unit-test"'
                sh 'pwd'
                sh 'ls -lrt'
                sh "cd jenkins-unit-test && ${env.M2_HOME}/bin/mvn clean compile test"

            }
        } 
       
    }
    post {
        failure {
            //emailext body: 'A Test EMail', recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']], subject: 'Test'

             emailext (
                subject: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                body: """<p>STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
                <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>&QUOT;</p>""",
                recipientProviders: [[$class: 'DevelopersRecipientProvider']]
            )
        }
    }
}

