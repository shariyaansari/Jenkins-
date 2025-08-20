pipeline {
    agent any

    tools {
        // Confirms the tool names match your Jenkins configuration
        maven 'Maven' 
        jdk 'JDK11'   
    }

    stages {
        stage('Build, Test & Package') {
            steps {
                echo 'Building, testing, and packaging the application...'
                // The 'package' goal will automatically run 'clean', 'compile', and 'test'.
                sh 'mvn clean package'
            }
        }
        
        stage('Archive Artifacts') {
            steps {
                echo 'Archiving the generated JAR file...'
                // This step saves the JAR as a build artifact for easy access.
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo '🎉 Pipeline completed successfully! The JAR file is ready.'
        }
        failure {
            echo '❌ Pipeline failed! Check the logs for details.'
        }
    }
}