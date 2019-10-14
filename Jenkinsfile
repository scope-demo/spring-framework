pipeline {
    agent none
    stages {
        stage('Build') {
            agent { docker 'openjdk:8-jdk' }
            steps {
                sh 'pwd'
                sh 'ls -la'
                sh 'rm -rf .gradle'
                sh 'ls -la'
                sh './gradlew cleanTest test --info --rerun-tasks'
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
