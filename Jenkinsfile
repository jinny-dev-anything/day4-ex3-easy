pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Install') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'pip3 install --quiet pytest'
                    } else {
                        bat 'pip install --quiet pytest'
                    }
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'python3 -m pytest -v test_main.py::test_greet'
                    } else {
                        bat 'python -m pytest -v test_main.py::test_greet'
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'echo Deploying to production...'
                    } else {
                        bat 'echo Deploying to production...'
                    }
                }
            }
        }
    }
    post {
        always {
            echo '파이프라인 종료'
        }
        success {
            echo '테스트 완료: 모든 테스트를 통과했습니다.'
        }
        failure {
            echo '테스트 실패'
        }
    }
}
