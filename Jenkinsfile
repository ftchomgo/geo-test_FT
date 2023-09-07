pipeline{
    agent any
    tools{
        maven 'M2_HOME'
    }
    stages{
        stage('maven clean'){
            steps{
              sh 'mvn clean'
            }
        }
        stage('maven install'){
            steps{
               sh 'mvn install'
            }
        }
        stage('maven package'){
            steps{
               sh 'mvn package'
            }
        }
        stage('upload artifact'){
            steps{
               nexusArtifactUploader artifacts: [[artifactId: 'bioMedical', 
               classifier: '', file: 'target/bioMedical-0.0.1-SNAPSHOT.jar',
                type: 'jar']], credentialsId: 'nexusID', groupId: 'QA',
                 nexusUrl: '198.58.119.40:8081/repository/FT_repo/',
                  nexusVersion: 'nexus3', protocol: 'http', repository: 'FT_repo', 
                  version: '0.0.1'
            }
        }
    }
}