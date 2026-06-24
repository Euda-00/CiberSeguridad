pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Compilando y preparando el entorno...'
            }
        }
        stage('Test') {
            steps {
                echo 'Ejecutando pruebas unitarias básicas...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Desplegando la aplicación en el entorno de pruebas...'
            }
        }
    }
}