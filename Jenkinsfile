import java.time.*

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
                //DisplayName()
                script {
                    println("Hello world!")
			        println "Branch name: ${BRANCH_NAME}"
                    println "This is build #${BUILD_NUMBER}"
                    println "URL for Jenkins: ${JENKINS_URL}"
                    //println "URL for this Job: ${JOB_URL}"
		
		// Sprint Script:
println ("Hello from Groovy!")

		def now = LocalDate.now()
println ("Today's date: ${now}")

def sprintEndDate = LocalDate.of(2020,06,30)
def beforeSprintEndDate = LocalDate.of(2020,06,29)
def afterSprintEndDate = LocalDate.of(2020,07,01)

println ("Sprint's end date: ${sprintEndDate}")
println ("Date before the end of the sprint: ${beforeSprintEndDate}")
println ("Date after the end of the sprint: ${afterSprintEndDate}")
                    
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
    
