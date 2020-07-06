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
        def buildPrefix = "BLD"
        def buildSuffix = "XX"

        // Captures week number of the year
        int weekOfYear = ofDate.get(IsoFields.WEEK_OF_WEEK_BASED_YEAR)
        // last day of sprint are always on Tuesdays
        def lastDayOfSprint = ofDate.with(DayOfWeek.TUESDAY)

        // if week is ODD
        if(weekOfYear % 2 != 0) {
            // if day of the week is after Tuesday
            if(ofDate.getDayOfWeek().getValue() > 2) {
                // adds two weeks to the odd week to land the last sprint day on a tuesday
                lastDayOfSprint = lastDayOfSprint.plus(14, ChronoUnit.DAYS).with(DayOfWeek.TUESDAY)
            }
            // if day of the week is on or before Tuesday
            else { // if(ofDate.getDayOfWeek().getValue() <= 2)
                // last day of sprint is in the week of the date
                lastDayOfSprint = ofDate.with(DayOfWeek.TUESDAY)
            }
        }
        // if week is EVEN
        else { // if(weekOfYear % 2 == 0)
            // adds a week to the even week to land the last sprint day on a tuesday in the following odd week
            lastDayOfSprint = lastDayOfSprint.plus(7, ChronoUnit.DAYS).with(DayOfWeek.TUESDAY)
        }

        println("${buildPrefix}${lastDayOfSprint}${buildSuffix}")
        return "${buildPrefix}${lastDayOfSprint}${buildSuffix}".toString()
    }
// end of script
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
    
