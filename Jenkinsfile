pipeline {
    agent {
        node {
            label "agent-1"
        }
    }  // Runs on any available agent
    environment{
        greeting= "hello jenkins"
    }
    options {
        timeout(time: 1, unit: 'SECONDS') 
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }

        stage('Deploy') {
            steps {
                sh"""
                    echo 'here i wrote the shell script'
                    echo $greeting
                    sleep 10
                """
            }
        }
    }
    post {
        success {
            echo "Step 1: Running post-build step for SUCCESS..."
            // Add your success-related commands here
        }
        failure {
            echo "Step 2: Running post-build step for FAILURE..."
            // Add your failure-related commands here
        }
        always {
            echo "Step 3: Running post-build step that always runs..."
            // Add commands that should always run (cleanup, notifications, etc.)
        }
    }
}
