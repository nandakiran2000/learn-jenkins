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
        timeout(time: 10, unit: 'SECONDS') 
        // disableConcurrentBuilds()
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
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
                    #sleep 10
                """
            }
        }
        stage('Params'){
            steps {
                sh """
                    echo "Hello ${params.PERSON}"

                    echo "Biography: ${params.BIOGRAPHY}"

                    echo "Toggle: ${params.TOGGLE}"

                    echo "Choice: ${params.CHOICE}"

                    echo "Password: ${params.PASSWORD}" 
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
