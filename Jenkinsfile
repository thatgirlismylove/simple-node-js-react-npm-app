pipeline {
    agent {
        docker {
            image 'node:lts-buster-slim'
            args '-p 3000:3000'
        }
    }

    parameters {
        choice(name: 'BUILD_ENV', choices: ['development', 'testing', 'production'], description: '请选择打包环境')
    }

    stages {
        stage('Install') { 
            steps {
                sh 'npm install' 
            }
        }
        stage('Build') {
            script {
                if (params.BUILD_ENV == 'development') {
                    sh 'npm run build:dev'
                } else if (params.BUILD_ENV == 'testing') {
                    sh 'npm run build:test'
                } else if (params.BUILD_ENV == 'production') {
                    sh 'npm run build:prod'
                }
            }
        }
    }
}