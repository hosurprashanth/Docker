properties([parameters([choice(choices: ['main', 'dev'], name: 'branch')])])

pipeline {
  agent {
    label 'agent1'
  }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub')
  }
  stages {
    stage('Build') {
      steps {
        sh "echo hello world"
      	// git branch: "main", url: 'https://github.com/hosurprashanth/Docker.git'
        // sh 'docker build -t nginx/nginx-docker .'
      }
    }
    stage('Login') {
      steps {
        sh "echo $DOCKERHUB_CREDENTIALS, $DOCKERHUB_CREDENTIALS_USR, $DOCKERHUB_CREDENTIALS_PSW"
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push nginx/nginx-docker'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
