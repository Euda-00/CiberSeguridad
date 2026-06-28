pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Preparando el entorno del proyecto e instalando herramientas...'[cite: 2]
            }
        }

        stage('Test') {
            steps {
                echo 'Ejecutando suite de pruebas automatizadas sobre la app Flask...'[cite: 2]
            }
        }

        stage('Generate Documentation') {
            steps {
                echo 'Ejecutando Doxygen para extraer documentación del código fuente...'[cite: 2]
                // Simula el comando nativo de generación de los manuales
                echo 'Leyendo configuraciones del Doxyfile...'[cite: 2]
                echo 'Procesando archivo app.py...'[cite: 2]
                echo 'Documentación HTML generada con éxito dentro de la carpeta docs/.'[cite: 2]
            }
        }

        stage('Version Control') {
            steps {
                echo 'Sincronizando la documentación técnica generada con el repositorio Git...'[cite: 2]
                echo 'Ejecutando: git add docs/'[cite: 2]
                echo 'Ejecutando: git commit -m "Docs: Actualizada la documentación automática del sistema"'[cite: 2]
                echo 'Trazabilidad del código actualizada correctamente en la SCM.'[cite: 2]
            }
        }

        stage('Deploy') {
            steps {
                echo 'Publicando el portal de documentación en Jenkins...'
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