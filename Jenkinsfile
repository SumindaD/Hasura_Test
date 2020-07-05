pipeline {
    agent { docker { 
            image 'hasura/graphql-engine:latest' 
            args '--privileged'
        } 
    }
    stages {
        stage('build') {
            steps {
                sh 'hasura version'
                sh 'hasura migrate apply'
                sh 'hasura metadata apply'
            }
        }
    }
}