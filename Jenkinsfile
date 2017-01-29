pipeline {
    agent {
      docker 'frekele/gradle:3.3-jdk8'
    }
    stages {
        stage("build and test") {
            steps {
                sh 'gradle build'
            }
        }
    }
}
