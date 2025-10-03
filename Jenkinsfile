pipeline {
    // TODO We could use docker here and specify the image, if possible
    agent any
    stages{
        stage('Checkout') {
            // Only perform a shallow checkout, saving space, network usage, and time
            checkout scmGit(
                branches: [[name: '$GIT_LOCAL_BRANCH']],
                extensions: [ cloneOption(shallow: true) ],
                userRemoteConfigs: [[url: 'https://github.com/LightGuard/incubator-kie-drools.git' ]]
            )
        }
        stage('Build') {
            withMaven {
                sh 'mvn clean install -DskipTests -Dfull'  
            }
        }
    }
}
