pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    } 
environment {
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
   
        // Stage3 : Publish the to Nexus
        stage ('Publish to Nexus') {
            steps {

            nexusArtifactUploader artifacts:
            [[artifactId: "${ArtifactId}",
            classifier: '',
            file: 'target/spring-petclinic-2.4.5.jar',
            type: 'jar']],
            credentialsId: '826640f8-3af5-43f8-9c7d-adfa35fbd2fc',
            groupId: "${GroupId}",
            nexusUrl: '10.0.0.105:8081',
            nexusVersion: 'nexus3',
            protocol: 'http',
            repository: 'Course-work-Release',
            version: "${Version}"
        }
        }
        
        // Stage4 : Deploing
        stage ('Deploy') {
            steps {
                echo "deploing ...."
            }
        }


    }

}