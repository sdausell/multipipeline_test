
pipeline {
    agent any
    stages {
        stage('SCM') {
            steps {
                git url: 'https://github.com/sdausell/multipipeline_test.git'
            }
        }
        stage('build && SonarQube analysis') {
            steps {
                withSonarQubeEnv('sonarqube') {
                    // Optionally use a Maven environment you've configured already
                    withMaven(maven:'Maven 3.8.4') {
                        sh 'mvn clean package sonar:sonar'
                    }
                }
            }
        }

}
