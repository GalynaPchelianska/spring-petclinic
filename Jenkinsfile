pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
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
   
        // Stage3 : Publish the to Nexus
        stage ('Publish to Nexus') {
            steps {

            }nexusArtifactUploader artifacts: [[artifactId: 'Coursework', classifier: '', file: 'target/Coursework-0.0.4-SNAPSHOT.jar', type: 'jar']], credentialsId: '26ca66ec-babc-452e-b678-0a010ddad642', groupId: 'com.coursework', nexusUrl: '10.0.0.105:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'maven-snapshots', version: '0.0.4-SNAPSHOT'
        }
        // Stage4 : Deploing
        stage ('Deploy') {
            steps {
                echo "deploing ..."
            }
        }


    }

}