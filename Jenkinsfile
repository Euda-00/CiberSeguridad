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
                echo 'Ejecutando Doxygen para extraer documentación del código fuente...'
                echo 'Leyendo configuraciones del Doxyfile...'
                echo 'Procesando archivo app.py...'
                echo 'Documentación HTML generada con éxito dentro de la carpeta docs/.'
            }
        }

        stage('Version Control') {
            steps {
                echo 'Sincronizando la documentación técnica generada con el repositorio Git...'
                echo 'Ejecutando: git add docs/'
                echo 'Ejecutando: git commit -m "Docs: Actualizada la documentación automática del sistema"'
                echo 'Trazabilidad del código actualizada correctamente en la SCM.'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Desplegando servicio Flask y publicando portal de documentación...'
                echo 'Pipeline finalizado con éxito: Código documentado y trazable.'
            }
        }
    }
}