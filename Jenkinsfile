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
      	// git branch: "main", url: 'https://github.com/hosurprashanth/Docker.git'
        sh 'docker build -t babbi87/prashanth_nginx:10 .'
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
        sh 'docker push babbi87/prashanth_nginx:10'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
      cleanWs()
    }
  }
}
