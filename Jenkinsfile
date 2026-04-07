pipeline {
    agent {
        label 'laravel'
    }

    stages {   // <-- all stages must be inside this block
        stage('Build') {
            steps {
                echo 'Building...'
                checkout scm

                echo 'Copying env file ...'
                sh 'cp .env.example .env'

                echo 'Configuring database...'
                // sh 'sed -i "s/DB_HOST=.*/DB_HOST=mysql/" .env'
                // sh 'sed -i "s/DB_PORT=.*/DB_PORT=3306/" .env'
                // sh 'sed -i "s/DB_DATABASE=.*/DB_DATABASE=laravel/" .env'
                // sh 'sed -i "s/DB_USERNAME=.*/DB_USERNAME=root/" .env'
                // sh 'sed -i "s/DB_PASSWORD=.*/DB_PASSWORD=root/" .env'

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