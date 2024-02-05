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
                sh 'mvn clean package -DskipTests'
            }
        }
//        stage('Static Code Analysis') {
//
//            steps {
//                withSonarQubeEnv(installationName: 'sonarqube') {
//                    sh 'mvn sonar:sonar '
//                }
//            }
//        }
        stage('docker build'){
            steps{
                sh 'docker build -t ashwiin11/spring-demo .'
                def dockerImage = docker.image("ashwiin11/spring-demo")
                withDockerRegistry(credentialsId: 'docker', url: 'https://index.docker.io/v1/') {
                    dockerImage.push()
                }

            }
        }
    }
}