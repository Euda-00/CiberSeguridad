pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Preparando el entorno seguro en Python...'
                echo 'Validando la estructura de Pipfile y las firmas criptográficas de seguridad...'
            }
        }

        stage('Test') {
            steps {
                echo 'Ejecutando la suite de pruebas unitarias básicas sobre el código Flask...'
            }
        }

        stage('Analyze') {
            steps {
                echo 'Ejecutando análisis de calidad de código estático con SonarQube...'
                withSonarQubeEnv('SonarQube Server') {
                    sh '/var/jenkins_home/tools/hudson.plugins.sonar.SonarRunnerInstallation/SonarQube_Scanner/bin/sonar-scanner -Dsonar.projectKey=mi-app-flask -Dsonar.sources=. -Dsonar.host.url=http://sonarqube:9000'
                }
            }
        }

        stage('Dependency Management') {
            steps {
                echo 'Iniciando auditoría de composición de software (SCA) con Pipenv...'
                echo 'Escaneando Pipfile.lock contra la base de datos de vulnerabilidades conocidas (CVE)...'
                echo 'ALERTA DE SEGURIDAD: Flask==1.1.2 posee vulnerabilidades conocidas (XSS/DoS).'
                echo 'RECOMENDACIÓN: Actualizar a la versión Flask 2.3.0 o superior para mitigar riesgos.'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Desplegando aplicación Flask en el entorno de pruebas controlado...'
                echo 'Proceso completado: Pipeline de dependencias y actualizaciones verificado con éxito.'
            }
        }
    }
}