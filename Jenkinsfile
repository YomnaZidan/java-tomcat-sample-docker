pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                bat 'mvn -f pom.xml clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }

        stage('Create Tomcat Docker Image'){
            steps {
                bat "cd"
                bat "ls -a"
                bat "docker build . -t tomcatsamplewebapp:${env.BUILD_ID}"
            }
        }

    }
}
