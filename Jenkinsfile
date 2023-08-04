properties([parameters([choice(choices: ['main', 'dev'], name: 'branch')])])

pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                // git branch: "main", url: 'https://github.com/hosurprashanth/Docker.git
                sh 'echo "given branch is $branch"'

                // Run Maven on a Unix agent.
                // sh "mvn -Dmaven.test.failure.ignore=true clean package"

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
    }
}
