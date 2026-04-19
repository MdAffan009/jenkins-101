pipeline {
    agent { label 'docker-agent-python' }

    triggers {
        pollSCM('H/5 * * * *')
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh '''
                    cd myapp
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install -r requirements.txt
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh '''
                    cd myapp
                    . venv/bin/activate
                    python3 hello.py
                    python3 hello.py --name=Robin
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                    echo "doing delivery stuff.."
                '''
            }
        }
    }
}
