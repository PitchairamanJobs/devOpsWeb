pipeline {
    agent any
    
    tools {
        maven 'local_maven'
    }
stages{
        stage('Build'){
            steps {
                bat 'mvn clean package'
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
            deploy adapters: [tomcat9(credentialsId: 'Tomcat', path: '', url: 'http://localhost:9090/')], contextPath: null, war: '**/*.war'
        }
    }
    }
}
