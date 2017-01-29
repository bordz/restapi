pipeline {
    agent { label 'docker' }
    stages {
        stage("prepare build scripts") {
            steps {
                sh 'pwd && ls -l'
                sh 'chmod +x ./gradlew'
            }
        }
        stage("build and push docker image") {
            steps {
                sh 'pwd && ls -l'
                sh 'cd ./build/docker/ && docker build -t xcoordinate/restapi . '
                sh 'cd ./build/docker/ && docker push xcoordinate/restapi'
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
