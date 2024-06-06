pipeline {
    agent any
    
    tools {
        // Install the Maven version configured as "mvn3.9.7" and add it to the path.
        maven "mvn3.9.7"
    }

    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/jenkins-docs/simple-java-maven-app.git'

                // Run Maven on a Unix agent.
                sh "mvn -Dmaven.test.failure.ignore=true clean package"
                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }

            post {
                // If Maven was able to run the tests, even if some of the tests failed,
                // record the test results and archive the jar file.
                success {
                    echo "Job Done"
                }
            }
        }
    }
}
