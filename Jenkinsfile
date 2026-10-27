
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Source code checked out from GitHub'
            }
        }

        stage('Test HTML Form') {
            steps {
                script {
                    def html = readFile('index.html')

                    if (!html.contains('<form')) {
                        error 'FAIL: Form element missing'
                    }
                    if (!html.contains('id="name"')) {
                        error 'FAIL: Name field missing'
                    }
                    if (!html.contains('id="email"')) {
                        error 'FAIL: Email field missing'
                    }
                    if (!html.contains('id="contact"')) {
                        error 'FAIL: Contact field missing'
                    }
                    if (!html.contains('type="submit"')) {
                        error 'FAIL: Submit button missing'
                    }

                    echo 'PASS: Form element exists'
                    echo 'PASS: Name field exists'
                    echo 'PASS: Email field exists'
                    echo 'PASS: Contact field exists'
                    echo 'PASS: Submit button exists'
                }
            }
        }
    }

    post {
        success {
            echo 'All HTML form tests passed!'
        }
        failure {
            echo 'HTML form tests failed!'
        }
    }
}
