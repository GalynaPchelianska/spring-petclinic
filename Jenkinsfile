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
        stage ('Publish to Nexus'){
            steps {
                script {
                    
 def NexusRepo = Version.endsWith("SNAPSHOT") : "Course-work-Release"
            nexusArtifactUploader artifacts:
            [[artifactId: "${ArtifactId}",
            classifier: '',
            file: "target/${ArtifactId}-${Build-number}.jar",
            type: 'jar']],
            credentialsId: '826640f8-3af5-43f8-9c7d-adfa35fbd2fc',
            groupId: "${GroupId}",
            nexusUrl: '10.0.0.105:8081',
            nexusVersion: 'nexus3',
            protocol: 'http',
            repository: 'Course-work-Release',
            version: "${Version}"
            build-number: "${Build-number}"
        }
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