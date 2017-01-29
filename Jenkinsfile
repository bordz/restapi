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
        }
        success {
            mail to:"x.coordinate@gmail.com", subject:"SUCCESS: ${currentBuild.fullDisplayName}", body: "Yay, we passed."
        }
        failure {
            mail to:"x.coordinate@gmail.com", subject:"FAILURE: ${currentBuild.fullDisplayName}", body: "Boo, we failed."
        }
        unstable {
            mail to:"x.coordinate@gmail.com", subject:"UNSTABLE: ${currentBuild.fullDisplayName}", body: "Huh, we're unstable."
        }
        changed {
            mail to:"x.coordinate@gmail.com", subject:"CHANGED: ${currentBuild.fullDisplayName}", body: "Wow, our status changed!"
        }
    }
}
