pipeline {
    agent any
    triggers { pollSCM('* * * * *') }
    stages {
        // IMPLICIT CHECKOUT STAGE:
        // stage('Checkout') {
        //      steps {
        //          git url: 'https://github.com/BiniamEyakem/jgsu-spring-petclinic.git', 
        //          branch: 'main'
        //      }         
        // }
        stage('Build') {
            steps {                
                bat 'mvn clean package'
            }
        }
    }
    // POST after stages, for entire pipeline, is also an implicit step albeit
    // with implicit config here, unlike implicit checkout stage
    post {
        always {
            junit '**/target/surefire-reports/TEST-*.xml'
            archiveArtifacts 'target/*.jar'
        }
    }
}
