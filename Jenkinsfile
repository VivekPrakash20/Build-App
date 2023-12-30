pipeline{
    agent any
    stages{
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo 'Archiving Artifacts'
                    archiveArtifacts artifacts:'**/target/*.war'
                }
            }

        }
        stage("Deploy into tomcat"){
            steps{
               deploy adapters: [tomcat9(credentialsId: 'c152d21d-94f0-432c-bedf-2f08bc2ee354', path: '', url: 'http://3.237.80.236:8083/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
