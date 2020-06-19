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
/*
println ("Hello from Groovy!")

def now = LocalDate.now()
println ("Today's date: ${now}")

def sprintEndDate = LocalDate.of(2020,06,30)
def beforeSprintEndDate = LocalDate.of(2020,06,29)
def afterSprintEndDate = LocalDate.of(2020,07,01)

println ("Sprint's end date: ${sprintEndDate}")
println ("Date before the end of the sprint: ${beforeSprintEndDate}")
println ("Date after the end of the sprint: ${afterSprintEndDate}")
*/
// Beginning of script from sprintMethod.groovy in /IdeaProject/GroovyProject2
// Syntax modified to run on Jenkins pipeline
public class Sprint {
    // variables
    def dateNow = LocalDate.now();
    def weekday = LocalDate.parse("${dateNow}").getDayOfWeek();
    def monthName = LocalDate.parse("${dateNow}").getMonth();
    int monthDay = LocalDate.parse("${dateNow}").getDayOfMonth();
    int year = LocalDate.parse("${dateNow}").getYear();
    def sprintEndDate = LocalDate.of(2020, 06, 30)
    def beforeSprintEndDate = LocalDate.of(2020, 06, 29)
    def afterSprintEndDate = LocalDate.of(2020, 07, 01)

    // method for today's date
    public static void todayDate() { // dynamic
        println("Today's date: ${dateNow}")
        println("Today is: ${weekday}")
        println("The month is: ${monthName}")
        println("The day of the month is: ${monthDay}")
        println("The year is: ${year}")
        println("Today is ${weekday}, ${monthName} ${monthDay}, ${year}")
    }

    // method for sprint date
    public static void sprintDate() {
        println("Sprint's end date: ${sprintEndDate}")
        println("Date before the end of the sprint: ${beforeSprintEndDate}")
        println("Date after the end of the sprint: ${afterSprintEndDate}")

        // This method cannot be run on Jenkins. May need to be more specific.
        def daysRemaining = sprintEndDate - dateNow
        println("Days remaining until end of sprint: ${daysRemaining}")
    }

}

// New instance of Sprint
Sprint s = new Sprint()
// Calling the new instances
s.todayDate()
s.sprintDate()
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
    
