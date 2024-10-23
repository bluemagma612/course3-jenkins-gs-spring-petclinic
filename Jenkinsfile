pipeline {
    agent any
    
    stages {    
        stage("build") {
            steps {
                sh "./mvnw package"
            }
        }
        stage("capture") {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar', followSymlinks: false
                junit stdioRetention: '', testResults: '**/target/surefire-reports/TEST*.xml'
                jacoco()
            }
        }
    }
}
