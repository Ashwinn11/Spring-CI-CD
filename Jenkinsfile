pipeline{
    agent {
        docker {
            image 'abhishekf5/maven-abhishek-docker-agent:v1'
            args '--user root -v /var/run/docker.sock:/var/run/docker.sock'
        }
    }
    stages{
        stage("git checkout"){
            steps{
                sh 'echo checkout passed'
            }
        }
        stage('mvn build'){
            steps{
                sh 'mvn clean build -DskipTests'
            }
        }
    }
}