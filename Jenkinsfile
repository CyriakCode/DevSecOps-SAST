pipeline {
    agent any

    //Definición de variables de entorno
    environment {
        PROJECT_DIR_NAME='DemoSnykPipeline'
        REPO_URL='https://github.com/CyriakCode/DevSecOps-SAST'
        REPO_REPORTES_USER='kbriones'
        REPO_REPORTES_URL='dev.azure.com/kbriones/NTTDATA%20CLOUD%20SECURITY/_git/ReportesHimeji'
        SONAR_HOST_URL='http://44.216.31.35:9000'
    }
    
    tools {
        maven 'maven_3_5_2'
    }
    stages {
        stage ('Run SCA Scan') {
            steps {
                withCredentials([string(credentialsId: 'SNYK_TOKEN', variable: 'SNYK_TOKEN')]) {
                    sh 'mvn snyk:test -fn'
                }
            }
        }
    }
}
