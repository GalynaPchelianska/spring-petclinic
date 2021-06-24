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

            nexusArtifactUploader artifacts: [[artifactId: 'spring-petclinic', classifier: '', file: 'target/Course-work-snapshot-2.4.5.jar', type: 'jar']], credentialsId: '26ca66ec-babc-452e-b678-0a010ddad642', groupId: 'org.springframework.samples', nexusUrl: '10.0.0.105:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'Course-work-snapshot', version: '2.4.5'
        }
        }
        // Stage4 : Deploing
        stage ('Deploy') {
            steps {
                echo "deploing ..."
            }
        }


    }

}