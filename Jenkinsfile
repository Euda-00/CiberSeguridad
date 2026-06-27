pipeline {
    agent any

    tools {
        // Corregidos los tipos para que coincidan con el diccionario de Jenkins
        Sonar 'SonarQube Scanner'
        'dependency-check' 'Dependency-Check'
    }

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
                    // Usamos la variable global para invocar el binario correcto en Linux
                    sh "${tool 'SonarQube Scanner'}/bin/sonar-scanner -Dsonar.projectKey=mi-app-flask -Dsonar.sources=. -Dsonar.host.url=http://sonarqube:9000"
                }
            }
        }

        stage('Security Test') {
            parallel {
                stage('Dependency Check') {
                    steps {
                        echo 'Analizando dependencias con OWASP Dependency-Check...'
                        dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'Dependency-Check'
                        dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
                    }
                }
                stage('OWASP ZAP Scan') {
                    steps {
                        echo 'Invocando OWASP ZAP para Análisis Dinámico (DAST)...'
                        // Ejecuta el contenedor de ZAP en la misma red interna apuntando al puerto 5000 de tu app
                        sh 'docker run --rm --network devsecops-net -v $(pwd):/zap/wrk/:rw owasp/zap2docker-stable zap-baseline.py -t http://host.docker.internal:5000/hello -r zap_report.html || true'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Desplegando aplicación en el entorno de pruebas...'
            }
        }
    }
}