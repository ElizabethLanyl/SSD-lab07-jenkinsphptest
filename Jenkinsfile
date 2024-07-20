pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    docker.image('php:7.4-cli').inside {
                        sh 'curl -sS https://getcomposer.org/installer | php'
                        sh 'php composer.phar install'
                    }
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    docker.image('php:7.4-cli').inside {
                        sh 'vendor/bin/phpunit tests'
                    }
                }
            }
        }
    }
}