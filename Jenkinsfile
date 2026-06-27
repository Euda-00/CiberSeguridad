pipeline {
    agent any

    tools {
        // Estos nombres deben coincidir con lo que configures en Jenkins
        sonarRunner 'SonarQube Scanner'
        dependencycheck 'Dependency-Check'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Preparando el entorno e instalando dependencias virtuales...'
                // Aquí simulas o instalas los requerimientos
                // sh 'pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                echo 'Ejecutando pruebas unitarias básicas...'
                // Espacio para tests automáticos si tuvieses
            }
        }

        stage('Analyze') {
            steps {
                echo 'Ejecutando análisis de calidad con SonarQube...'
                // Envía el código a SonarQube
                withSonarQubeEnv('SonarQube Server') {
                    sh 'sonar-scanner'
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
                        // Ejecuta el contenedor de ZAP contra la URL donde corre tu app Flask
                        sh 'docker run --rm -v $(pwd):/zap/wrk/:rw owasp/zap2docker-stable zap-baseline.py -t http://localhost:5000/hello -r zap_report.html || true'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Desplegando aplicación en el entorno de pruebas...'
                // Comando para dejar corriendo la app Flask en background o en un contenedor
                // sh 'python app.py &'
            }
        }
    }
}