pipeline {
    // TODO We could use docker here and specify the image, if possible
    agent any
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/LightGuard/incubator-kie-drools.git', branch: 'jenkinsfile'
            }
        }
        stage('Build') {
            agent {
                docker { image 'maven:3.9.11-eclipse-temurin-17' }
            }
            steps {
                withMaven {
                    sh 'mvn clean install -DskipTests -Dfull'  
                }
            }
        }
    }
}
