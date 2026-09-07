pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'git@github.com:shivadixt/portfolio-site.git'
            }
        }

        stage('Deploy to Apache') {
            steps {
                sh '''
                    sudo cp -r * /var/www/html/
                    sudo systemctl reload apache2
                '''
            }
        }
    }

    post {
        success {
            echo 'Portfolio site deployed successfully to Apache2!'
        }
        failure {
            echo 'Deployment failed — check the logs above.'
        }
    }
}
