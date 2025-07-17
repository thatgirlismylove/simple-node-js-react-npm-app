pipeline {
    agent {
        docker {
            image 'node:lts-buster-slim'
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
               sh 'npm run build' 
            }
            
        }
    }
}