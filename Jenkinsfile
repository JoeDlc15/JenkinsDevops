pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                // 1. Descargamos el código primero
                git branch: 'main', url: 'https://github.com/JoeDlc15/DevopsProyect.git'
                
                // 2. Usamos un bloque script para ejecutar comandos y guardar variables
                script {
                    // Obtenemos el nombre del autor del último commit
                    def author = sh(script: "git log -1 --pretty=format:'%an'", returnStdout: true).trim()
                    
                    // Imprimimos el nombre en la consola
                    echo "------------------------------------------------"
                    echo "🚀 El commit fue realizado por: ${author}"
                    echo "------------------------------------------------"
                    
                    // Opcional: Agregar el nombre a la descripción del Build en Jenkins (para verlo en el dashboard)
                    currentBuild.description = "Commit por: ${author}"
                }
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
                // Aseguramos que existe el directorio antes de comprimir (buena práctica)
                sh 'if [ -d "./src" ]; then zip -r release.zip ./src; else echo "Directorio src no encontrado"; fi'
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
            // Solo archivamos si el archivo existe
            script {
                if (fileExists('release.zip')) {
                    archiveArtifacts artifacts: 'release.zip', fingerprint: true
                    echo "Release generado exitosamente."
                }
            }
        }
        failure {
            echo "Falló el release."
        }
    }
}