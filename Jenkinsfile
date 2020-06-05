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
                    println("Hello world!")
			        println "Branch name: ${BRANCH_NAME}"
                    println "This is build #${BUILD_NUMBER}"
                    println "URL for Jenkins: ${JENKINS_URL}"
                    //println "URL for this Job: ${JOB_URL}"
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

