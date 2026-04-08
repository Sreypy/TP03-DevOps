pipeline {
    agent {
        label 'laravel'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository...'
                git 'https://github.com/Sreypy/TP03-DevOps.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Copying env file ...'
                sh 'cp .env.example .env'

                echo 'Installing dependencies...'
                sh 'composer install'
                sh 'npm install'

                echo 'Generating application key...'
                sh 'php artisan key:generate'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'php artisan test'
            }
        }
    }
}