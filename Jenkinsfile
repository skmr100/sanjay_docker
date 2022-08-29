pipeline {
    options {
        timeout(time: 1, unit: 'HOURS')
    }
    agent {
        label 'ubuntu-1804 && amd64 && docker'
    }
    stages {
        stage('build') {
            when {
                branch 'master'
            }
            sh "docker build -t skmr100/getting-started ."
        }
        stage('push') {
            withDockerRegistry([url: "", credentialsId: "dockerbuildbot-index.docker.io"]) {
                echo "Login Successful"
                sh("docker push skmr100/getting-started") {
                    echo "Imaged Pushed"
                }

            }
                
        }
    }
}
