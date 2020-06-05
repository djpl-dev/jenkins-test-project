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
                    
                }
            }
        }
	stage('Example Deploy') {
            when {
                branch 'production'
                println "${BUILD_NUMBER}"
            }
            steps {
                echo 'Deploying'
            }
        }
   }
}

