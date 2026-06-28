pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Preparando el entorno del proyecto...'
            }
        }

        stage('Test') {
            steps {
                echo 'Ejecutando pruebas sobre la app Flask...'
            }
        }

        stage('Generate Documentation') {
            steps {
                echo 'Invocando Doxygen real a través del socket de Docker...'
                sh 'docker run --rm -v \$(pwd):/data miatlabs/doxygen doxygen Doxyfile'
            }
        }

        stage('Version Control') {
            steps {
                echo 'Verificando la existencia de los archivos generados...'
                sh 'ls -la docs/html/'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Publicando el portal de documentación web real en Jenkins...'
                publishHTML([
                    allowMissing: false,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: 'docs/html',
                    reportFiles: 'index.html',
                    reportName: 'Documentación Técnica Doxygen'
                ])
            }
        }
    }
}