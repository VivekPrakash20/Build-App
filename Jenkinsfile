pipeline{
    agent any
    stages{

        stage{
            steps('code test'){
                sh 'mvn test'
            }
        }
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
                          deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://54.176.196.91:9090/')], contextPath: null, onFailure: false, war: '**/*.war'
            }
        }
    }
}
