pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/lesantivanez/jenkins-release-demo.git'
            }
        }
        stage('Build') {
            steps {
                sh 'echo "Compilando aplicación..."'
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Ejecutando pruebas..."'
            }
        }
        stage('Package Release') {
            steps {
                sh 'echo "Generando artefacto release..."'
                sh 'zip zipFile: release.zip ./build/libs/*'
            }
        }
        stage('Publish Artifact') {
            steps {
                sh 'echo "Publicando artefacto..."'
            }
        }
    }
    post {
        success { echo "Release generado exitosamente." }
        failure { echo "Falló el release." }
    }
}