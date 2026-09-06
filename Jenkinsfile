pipeline {
    agent {
        label 'agent1'
    }

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
                sh 'pkill -f "python3 -m http.server" || true'
                sh 'nohup ./run.sh &'
                sh 'sleep 5'
                sh 'curl -s http://localhost:8000 || echo "Server check done"'
            }
        }
    }

    post {
        success {
            echo "Pipeline completed"
        }

        failure {
            echo "Pipeline failed"
        }

        always {
            echo "Killing server"
            sh 'pkill -f "python3 -m http.server" || true'
        }
    }
}
