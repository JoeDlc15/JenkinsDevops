pipeline {
    agent {
        docker {
            image 'santiluis/jenkins-unzip:TAG'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }

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
                sh 'zip -r release.zip ./src'
            }
        }

        stage('Publish Artifact') {
            steps {
                sh 'echo "Publicando artefacto..."'
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: 'release.zip', fingerprint: true
            echo "Release generado exitosamente."
        }
        failure {
            echo "Falló el release."
        }
    }
}
