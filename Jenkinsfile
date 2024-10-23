pipeline {
    agent any
    
    stages {    
        stage("checkout") {
            steps {
                git branch:"main", url: "https://github.com/bluemagma612/course3-jenkins-gs-spring-petclinic"
            }
        }
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
