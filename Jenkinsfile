pipeline{
    agent any
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