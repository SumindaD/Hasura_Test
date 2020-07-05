pipeline {
    agent { docker { 
            image 'hasura/graphql-engine:latest' 
            args '--privileged'
        } 
    }
    stages { 
        stage('Initialize'){
            def dockerHome = tool 'DockerInstallation'
            env.PATH = "${dockerHome}/bin:${env.PATH}"
        },
        stage('build') {
            steps {
                sh 'hasura version'
                sh 'hasura migrate apply'
                sh 'hasura metadata apply'
            }
        }
    }
}