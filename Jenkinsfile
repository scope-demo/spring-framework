pipeline {
    agent none
    stages {
        stage('Build') {
            agent { docker 'openjdk:8-jdk' }
            steps {
                //sh './gradlew cleanTest test --rerun-tasks'
                sh 'ls -la'
                sh 'pwd'
            }
        }
    }

    post {
        always {
            node('master') {
                 archiveArtifacts artifacts: '/var/log/scope/scope_*.log'
                 sh 'rm -f scope_*.log'
            }
        }
    }
}
