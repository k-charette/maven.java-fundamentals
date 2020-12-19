pipeline {
    agent {
        docker {
            image 'jamesdbloom/docker-java8-maven:latest' 
            args '-v /root/.m2:/root/.m2' 
        }
    }
    stages {
        stage('Set Up') {
            steps {
                script {
                    sh 'rm -rf maven.java-fundamentals'
                }
            }
        }
        stage('SCM Checkout') {
            steps {
                sh 'git clone https://github.com/k-charette/maven.java-fundamentals $PWD/maven.java-fundamentals'
            }
        }
        stage('Compile-Package-Test') {
            steps {
                script {
                    dir('$PWD/maven.java-fundamentals') {
                        sh "mvn package -Dmaven.test.failure.ignore=true"
                    }
                }
            }
        }
    }
}

