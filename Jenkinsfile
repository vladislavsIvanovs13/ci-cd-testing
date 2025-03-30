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
                    deploy("dev", 7001)
                }
            }
        }
        stage('tests-on-dev') {
            steps {
                script {
                    test("dev")
                }
            }
        }
        stage('deploy-to-staging') {
            steps {
                script {
                    deploy("stg", 7002)
                }
            }
        }
        stage('tests-on-staging') {
            steps {
                script {
                    test("stg")
                }
            }
        }
        stage('deploy-to-preprod') {
            steps {
                script {
                    deploy("preprod", 7003)
                }
            }
        }
        stage('tests-on-preprod') {
            steps {
                script {
                    test("preprod")
                }
            }
        }
        stage('deploy-to-prod') {
            steps {
                script {
                    deploy("prod", 7004)
                }
            }
        }
        stage('tests-on-prod') {
            steps {
                script {
                    test("prod")
                }
            }
        }
    }
}

def install() {
    echo "Installing pip dependencies..."
    git branch: 'main', poll: false, url: 'https://github.com/mtararujs/python-greetings'
    bat "pip install -r requirements.txt"
}

def deploy(String env, int port) {
    echo "Deploying to ${env}..."
    git branch: 'main', poll: false, url: 'https://github.com/mtararujs/python-greetings'
    bat "npm init -y"
    bat "npm install pm2"
    bat "dir"
    bat "node_modules\\.bin\\pm2 delete greetings-app-${env} & EXIT /B 0"
    bat "node_modules\\.bin\\pm2 start app.py --name greetings-app-${env} -- --port ${port}"
}

def test(String env) {
    echo "Testing on ${env}..."
    git branch: 'main', poll: false, url: 'https://github.com/mtararujs/course-js-api-framework'
    bat "npm install"
    bat "dir"
    bat "npm run greetings greetings_${env}"
}