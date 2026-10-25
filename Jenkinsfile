pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Manjunath1210/demo-rep.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Checking website files'
                sh 'test -f index.html'
            }
        }

        stage('Test') {
            steps {
                sh 'grep -q "Sri Manjunadheshwara Hotel" index.html'
                sh 'grep -q "Chicken Biryani" index.html'
                echo 'All tests passed'
            }
        }

        stage('Deploy') {
            steps {
                sh 'sudo /usr/bin/install -m 644 index.html /var/www/html/index.html'
                echo 'Deployment successful'
            }
        }
    }
}
