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
        stage ('SonnarQube'){

            steps {
                echo 'Sending the projecto to sonarqube for code analysis'
            
 
                withSonarQubeEnv("sonarqube-server") { // You can override the credential to be used
                    sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
                }
            }
        }
        
    }

}