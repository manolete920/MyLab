pipeline{
    //Directives
    agent any
    tools {
        maven 'Maven-386'
    }

    stages {
        // Specify various stage with in stages

        // stage 1. Build
        stage ('Build'){
            steps {
                sh 'mvn clean install package'
            }
        }

        // Stage2 : Testing
        stage ('Test'){
            steps {
                echo ' testing......'

            }
        }

                // Stage3 : Publish the artifacts to Nexus
        stage ('Publish to Nexus'){
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpsLab', classifier: '', file: 'target/VinayDevOpsLab-0.0.3-SNAPSHOT.war', type: 'war']], credentialsId: '1d588803-6551-47e3-a1ce-b2c7e551fb12', groupId: 'com.vinaysdevopslab', nexusUrl: '172.20.10.105:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'VinaysDevOpsLab-SNAPSHOT', version: '0.0.3-SNAPSHOT'
            }
        }

        stage ('Deploy'){
            steps {
                echo ' deployin......'

            }
        }

        
    }

}