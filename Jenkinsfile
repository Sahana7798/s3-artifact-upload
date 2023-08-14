pipeline {
    agent any
    stages {
        stage ('Git checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Sahana7798/React-app.git'
            }
        }
        stage ('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }
        stage('uploadtos3') {
             steps {
                 withAWS(region:'us-east-1',credentials:'auto') {
               
                
                s3Upload(bucket: "autoscalenew", includePathPattern: "build/**")
                 }
             }
        }
    }
}
