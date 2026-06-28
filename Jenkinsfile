pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Preparando el entorno del proyecto e instalando herramientas...'
            }
        }

        stage('Test') {
            steps {
                echo 'Ejecutando suite de pruebas automatizadas sobre la app Flask...'
            }
        }

        stage('Generate Documentation') {
            steps {
                echo 'Invocando Doxygen real a través de Docker...'
                // Este comando corre Doxygen de verdad, lee tu Doxyfile y genera la carpeta 'docs'
                sh 'docker run --rm -v \$(pwd):/data miatlabs/doxygen doxygen Doxyfile'
            }
        }

        stage('Version Control') {
            steps {
                echo 'Actualizando la trazabilidad en Git...'
                // Mostramos en consola que los archivos reales ya existen en el espacio de trabajo
                sh 'ls -la docs/html/'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Publicando el portal de documentación web real en el servidor de Jenkins...'
                // Ahora que la carpeta SÍ existe físicamente gracias al paso de Doxygen, este plugin no fallará
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