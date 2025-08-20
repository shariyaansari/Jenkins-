pipeline {
    agent any

    tools {
        maven 'Maven'  // make sure Maven is configured in Jenkins (Manage Jenkins → Global Tool Configuration)
        jdk 'JDK11'    // same for Java (set up once in Jenkins)
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'mvn test'
            }
        }

        stage('Package/Deploy') {
            steps {
                echo 'Packaging application into JAR...'
                sh 'mvn package'
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
