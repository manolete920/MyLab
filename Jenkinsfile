pipeline{
    //Directives
    agent any
    tools {
        maven 'Maven-386'
    }

    environment{
       ArtifactId = readMavenPom().getArtifactId()
       Version = readMavenPom().getVersion()
       Name = readMavenPom().getName()
       GroupId = readMavenPom().getGroupId()
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
                //script {
                    //def NexusRepo = Version.endsWith("SNAPSHOT") ? "VinaysDevOpsLab-SNAPSHOT" : "VinaysDevOpsLab-RELEASE"
                    nexusArtifactUploader artifacts: 
                    [[artifactId: "${ArtifactId}", 
                    classifier: '', 
                    file: "target/${ArtifactId}-${Version}.war", 
                    type: 'war']], 
                    credentialsId: '1d588803-6551-47e3-a1ce-b2c7e551fb12', 
                    groupId: "${GroupId}", 
                    nexusUrl: '172.20.10.105:8081', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: "VinaysDevOpsLab-SNAPSHOT", 
                    version: "${Version}"
                //}
            
            }
        }

        stage ('Deploy'){
            steps {
                echo ' deployin......'

            }
        }

        
    }

}