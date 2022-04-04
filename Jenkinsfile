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
    echo 'Building Docker Image'
}
}
stage('Push Docker Image to Docker Hub') {
steps {
    echo 'Pushing Docker Image'
}
}
}
}
