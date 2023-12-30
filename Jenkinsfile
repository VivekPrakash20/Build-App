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
               deploy adapters: [tomcat9(credentialsId: '73a3deb9-c4d4-4dd3-a147-40d502ada23e', path: '', url: 'http://15.229.243.142:9090/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
