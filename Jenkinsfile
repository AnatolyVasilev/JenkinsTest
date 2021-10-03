pipeline {
    agent any
    stages {
        stage('Git-Checkout') {
            steps {
                echo "Checking out from Git Repo";
                git branch: 'main', url: 'https://github.com/AnatolyVasilev/JenkinsTest.git'
            }
        }
        stage('Build') {
            steps {
                sh 'bash ./Build.sh'
            }
        }
        stage('JUnit') {
            steps {
                sh 'bash ./Unit.sh'
            }
        }
        stage('Quality-Gate') {
            steps {
                sh 'bash ./Quality.sh'
            }
        }
        stage('Deploy') {
            steps {
                sh 'bash ./Deploy.sh'
            }
        }
    }
    post {
        always {
            echo 'This will allways run'
        }
        success {
            echo 'This will run only if success'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}