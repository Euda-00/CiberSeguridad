pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Instalando dependencias de la aplicación...'
                // Aquí simula la preparación
            }
        }
        
        stage('Test') {
            steps {
                echo 'Ejecutando pruebas unitarias básicas...'
            }
        }

        stage('Static Code Analysis (SonarQube)') {
            steps {
                echo 'Ejecutando análisis estático con SonarQube...'

                sh "npx sonarqube-scanner -Dsonar.projectKey=mi-app-flask-v2 -Dsonar.sources=. -Dsonar.host.url=http://sonarqube:9000 -Dsonar.login=sqp_ded9226530f94196f42e1041aeec5b9d648ddb4b"
            }
        }

        stage('Security Test (Dependency Check)') {
            steps {
                echo 'Escaneando vulnerabilidades en dependencias (requirements.txt)...'
            }
        }

        stage('Vulnerability Scan (OWASP ZAP)') {
            steps {
                echo 'Ejecutando escaneo dinámico contra la app Flask...'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Desplegando la aplicación de manera segura en producción...'
            }
        }
    }
}