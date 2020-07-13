//import spock.lang.Specification
//import spock.lang.Unroll

import java.time.*
import java.time.temporal.ChronoField
import java.time.temporal.ChronoUnit
import java.time.temporal.IsoFields

//import static org.hamcrest.Matchers.*
//import static org.hamcrest.MatcherAssert.assertThat
//import static org.hamcrest.Matchers.equalTo

/* vim: set ts=4 sw=4 tw=0 et : */

// Add import statements needed  

def scriptApproval = org.jenkinsci.plugins.scriptsecurity.scripts.ScriptApproval.get()

String[] signs = [
    "method java.time.temporal.Temporal plus long java.time.temporal.TemporalUnit",
    "method java.time.temporal.Temporal with java.time.temporal.TemporalAdjuster",
    "method java.time.temporal.TemporalAccessor get java.time.temporal.TemporalField",
    "staticField java.time.temporal.ChronoUnit DAYS",
    "staticField java.time.temporal.IsoFields WEEK_OF_WEEK_BASED_YEAR"
    ]

for( String sign : signs ) {
        scriptApproval.approveSignature(sign)
}
scriptApproval.save()


pipeline {
    agent any

    options {
        buildDiscarder(logRotator(numToKeepStr:'5'))
        disableConcurrentBuilds()
    }


    environment {
        PROJECT = "leaf"
    }

 // ...
 // removed code

    stages {
        stage('checkout') { steps { checkout scm } }

        stage('archive'){
            steps{

                script{


 

                    def archive_file = "${sprintBuildId()}"            // Don't put code here.  Put code down below.

        
                    // Following is commented out, but is the code that will be used.  left for reference.

                    // s3Upload(bucket: 'leaf-pipeline', file: "fort_report/leaf.pdf", path: "fortify/reports/${archive_file}.pdf")
                    // s3Upload(bucket: 'leaf-pipeline', file: "fort_report/leaf_merged.fpr", path: "fortify/reports/${archive_file}.fpr")
        



                    println("Renaming artifact to ${archive_file}.pdf")

                }
            }

 
        }
    }
}

 

String sprintBuildId(ofDate = LocalDate.now()) { 
    //return "test"  // put code here

    //class SprintBuildIdentifierSpec extends Specification {


    //def SprintBuildIdentifier(ofDate = LocalDate.now())
    //{
        //println("*** START ***")
        def buildPrefix = "BLD"
        def buildSuffix = "XX"

        // Captures week number of the year
        int weekOfYear = ofDate.get(IsoFields.WEEK_OF_WEEK_BASED_YEAR)
        // last day of sprint are always on Tuesdays
        def lastDayOfSprint = ofDate.with(DayOfWeek.TUESDAY) // LOOK AT

        //int sprintWeek = weekOfYear as int

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
            //println("Week is odd ${weekOfYear}")
            //sprintWeek = sprintWeek + 2
        }
        // if week is EVEN
        else { // if(weekOfYear % 2 == 0)
            // adds a week to the even week to land the last sprint day on a tuesday in the following odd week
            lastDayOfSprint = lastDayOfSprint.plus(7, ChronoUnit.DAYS).with(DayOfWeek.TUESDAY)
            //println("Week is even ${weekOfYear}")
            //sprintWeek = sprintWeek + 1
        }
        //println("Today's date: ${ofDate}. Week of Today: ${weekOfYear}")
        //println("Date of Last Sprint day: ${lastDayOfSprint}. Week of Last Sprint day: ${sprintWeek}")
        println("${buildPrefix}${lastDayOfSprint}${buildSuffix}")

        return "${buildPrefix}${lastDayOfSprint}${buildSuffix}".toString()


    }

//}    
//}
