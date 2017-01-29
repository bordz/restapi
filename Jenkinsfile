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
    post {
        always {
            archive "build/**/*"
            junit 'build/test-results/*.xml'
            junit 'build/reports/tests/*.xml'
        }
    }
}
