pipeline {
    agent any
    environment {
        PROJECT = "leaf"
    }

    stages {
        stage('checkout') { 
            steps {
                checkout scm 
            } 
        }
        stage('test') {
            steps {
                script {
                    println("hello world")
			        println "${BRANCH_NAME}"
                    println "${BUILD_NUMBER}"
                }
            }
        }
	stage('Example Deploy') {
            when {
                branch 'production'
                
            }
            steps {
                echo 'Deploying'
            }
        }
   }
}

