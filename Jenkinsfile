pipeline {
    agent {
        docker {
            image 'maven:3.8.1-adoptopenjdk-11' 
            args '-v /root/.m2:/root/.m2' 
        }
    }
    stages {
        stage('Build') { 
            stage('Test') {
                steps {
                    sh 'mvn test'
                }
                post {
                    always {
                    junit 'target/surefire-reports/*.xml'
                    }
                }
            }
                steps {
                    sh 'mvn -B -DskipTests clean package' 
                }
        }
    }
}
