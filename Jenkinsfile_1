pipeline{
    agent any
    
    tools {
        // auto installed maven
        maven "Maven"
    }
    
    stages{
        
        stage('Git Clone'){
            steps{
            git credentialsId:'github-credentials', branch:'main', url:'https://github.com/Yasnehinc/java_application.git'
            }
        }
        
        stage('Maven Build'){
            steps{
                sh 'mvn clean install'
            }
        }
        
        stage('Deploy'){
            steps{
                s3Upload consoleLogLevel: 'INFO', dontSetBuildResultOnFailure: false, dontWaitForConcurrentBuildCompletion: false, entries: [[bucket: 'nehemiah-devops-training', excludedFile: '', flatten: false, gzipFiles: false, keepForever: false, managedArtifacts: false, noUploadOnFailure: false, selectedRegion: 'us-east-2', showDirectlyInBrowser: false, sourceFile: 'target/*.jar', storageClass: 'STANDARD', uploadFromSlave: false, useServerSideEncryption: false]], pluginFailureResultConstraint: 'FAILURE', profileName: 'S3', userMetadata: []
            }
        }
    }
    
}
