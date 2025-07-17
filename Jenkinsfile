pipeline {
    agent {
        docker {
            image 'node:lts-alpine3.22'
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
            steps {
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
}