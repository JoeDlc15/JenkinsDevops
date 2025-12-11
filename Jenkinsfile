pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/JoeDlc15/JenkinsDevops.git'
            }
        }

        stage('Commit Info') {
            steps {
                sh '''
                    echo "====================================="
                    echo "      INFORMACIÓN DEL ÚLTIMO COMMIT"
                    echo "====================================="
                    echo "Autor:      $(git log -1 --pretty=format:'%an')"
                    echo "Email:      $(git log -1 --pretty=format:'%ae')"
                    echo "Fecha:      $(git log -1 --pretty=format:'%ad')"
                    echo "Mensaje:    $(git log -1 --pretty=format:'%s')"
                    echo "====================================="
                '''
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
