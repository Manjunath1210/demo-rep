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

        stage('Update Website') {
            steps {
                echo 'Updating hotel name'
                sh '''
                    sed -i 's/Sri Manjunadheshwara Hotel and fast food center/Sri Manjunadheshwara Hotel and fast food/g' index.html
                '''
            }
        }

        stage('Test') {
            steps {
                sh 'grep -q "Sri Manjunadheshwara Hotel and fast food" index.html'
                sh '! grep -q "Sri Manjunadheshwara Hotel and fast food center" index.html'
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
