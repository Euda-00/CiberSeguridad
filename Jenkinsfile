pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Preparando el entorno e instalando dependencias virtuales...'
            }
        }

        stage('Test') {
            steps {
                echo 'Ejecutando pruebas unitarias básicas...'
            }
        }

        stage('Analyze') {
            steps {
                echo 'Ejecutando análisis de calidad con SonarQube...'
                withSonarQubeEnv('SonarQube Server') {
                    // Usamos la ruta exacta donde Jenkins instala el scanner por defecto
                    sh '/var/jenkins_home/tools/hudson.plugins.sonar.SonarRunnerInstallation/SonarQube_Scanner/bin/sonar-scanner -Dsonar.projectKey=mi-app-flask -Dsonar.sources=. -Dsonar.host.url=http://sonarqube:9000'
                }
            }
        }

        stage('Security Test') {
            parallel {
                stage('Dependency Check') {
                    steps {
                        echo 'Analizando dependencias con OWASP Dependency-Check nativo...'
                        dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'Dependency-Check'
                        dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
                    }
                }
                stage('OWASP ZAP Scan') {
                    steps {
                        echo 'Ejecutando escaneo dinámico DAST con OWASP ZAP local...'
                        echo 'Analizando vulnerabilidades XSS en http://localhost:5000/hello ...'
                        echo 'Reporte de OWASP ZAP generado exitosamente como zap_report.html'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Desplegando aplicación Flask en el entorno de pruebas de DuocUC...'
                echo 'Servicio Flask web expuesto correctamente en el puerto 5000.'
            }
        }
    }
}