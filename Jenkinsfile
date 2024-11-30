pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                // Checkout from Git repository on the 'main' branch
                git branch: 'main', url: 'https://github.com/swathibandaa/lms'
            }
        }

        stage('Build') {
            steps {
                echo 'Compiling Java files...'
                bat 'javac Book.java Library.java LibrarySystem.java'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                bat 'javac -cp ".;C:\\Users\\Swathi\\OneDrive\\Desktop\\project\\junit-4.10.jar" LibrarySystemTest.java'
                bat 'java -cp ".;C:\\Users\\Swathi\\OneDrive\\Desktop\\project\\junit-4.10.jar" org.junit.runner.JUnitCore LibrarySystemTest'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                bat 'jar cvf LibrarySystem.jar Book.class Library.class LibrarySystem.class'
                bat 'xcopy /Y LibrarySystem.jar "C:\\Users\\Swathi\\OneDrive\\Desktop\\project\\"'
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}