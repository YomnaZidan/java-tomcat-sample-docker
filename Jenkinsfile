pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                exec 'mvn -f pom.xml clean package'
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
                exec "pwd"
                exec "ls -a"
                exec "docker build . -t tomcatsamplewebapp:${env.BUILD_ID}"
            }
        }

    }
}