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
                DisplayName()
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
/*
// simple groovy method
    class Example {
        static def DisplayName() {
            println("This is how methods work in groovy");
            println("This is an example of a simple method");
        } 
            
        static void main(String[] args) {
            DisplayName();
        } 
    } */
    