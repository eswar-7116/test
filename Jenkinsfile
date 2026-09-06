pipeline {
    agent any

    stages {
        stage("Checkout") {
            steps {
                checkout scm
            }
        }

        stage("Build") {
            steps {
                echo "Building..."
                sh "./build.sh"
            }
        }

        stage("Test") {
            steps {
                echo "Testing..."
                sh "./test.sh"
            }
        }

        stage("Start") {
            steps {
                echo "Starting..."
            }
        }
    }
}
