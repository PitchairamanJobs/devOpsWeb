pipeline {
    agent any
    
    tools {
        maven 'local_maven'
    }
stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Archiving the artifacts'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    stage ('Deploy to tomcat server'){
        steps{
            deploy adapters: [tomcat9(credentialsId: 'Tomcat-1', path: '', url: 'http://65.2.144.28:8080/')], contextPath: null, war: '**/*.war'
        }
    }
    }
}
