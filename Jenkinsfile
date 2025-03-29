pipeline {
    agent any

    stages {
        stage('install-pip-deps') {
            steps {
                script {
                    install()
                }
            }
        }
        stage('deploy-to-dev') {
            steps {
                script {
                    deploy("DEV")
                }
            }
        }
        stage('tests-on-dev') {
            steps {
                script {
                    test("DEV")
                }
            }
        }
        stage('deploy-to-staging') {
            steps {
                script {
                    deploy("STG")
                }
            }
        }
        stage('tests-on-staging') {
            steps {
                script {
                    test("STG")
                }
            }
        }
        stage('deploy-to-preprod') {
            steps {
                script {
                    deploy("PREPROD")
                }
            }
        }
        stage('tests-on-preprod') {
            steps {
                script {
                    test("STG")
                }
            }
        }
        stage('deploy-to-prod') {
            steps {
                script {
                    deploy("PROD")
                }
            }
        }
        stage('tests-on-prod') {
            steps {
                script {
                    test("PROD")
                }
            }
        }
    }
}

def install() {
    echo "Installing pip dependencies..."
    // git branch: 'main', poll: false, url: 'https://github.com/mtararujs/python-greetings'
    bat "python --version"
    // bat "pip install -r requirements.txt"
}

def deploy(String env) {
    echo "Deploying to ${env}..."
}

def test(String env) {
    echo "Testing on ${env}..."
}