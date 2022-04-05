pipeline {
    agent any

    stages {
        stage('CheckOut') {
            steps {
                echo 'Checking out'
            }
        }
            stage('Package') {
            steps {
                bat 'mvn clean package'
            }
            }
            stage('JaCoCo Report') {
            steps {
               jacoco()
            }
        }
        stage('sonar analysis') {
            steps {
            withSonarQubeEnv('ZensarCodeAnalysis'){
            bat 'mvn sonar:sonar'
            }
        }   
    }
       stage('Build Docker Image') {
steps {
    bat 'docker build -t sathish/6456/test .'
}
}
stage('Push Docker Image to Docker Hub') {
steps {
    bat 'docker login -u username -p password'
    bat 'docker push sathish6456/test'
}
}
}
}
