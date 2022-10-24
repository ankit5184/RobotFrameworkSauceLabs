pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: "main", url:'https://github.com/ankit5184/RobotFrameworkSauceLabs.git'
            }
        }
        stage('Test') {
            steps{
                bat 'run.bat'
            }
        }
    }
   post {
//         	always {
// 		        script {
// 		          step(
// 			            [
// 			              $class              : 'RobotPublisher',
// 			              outputPath          : 'Results1',
// 			              outputFileName      : '**/output.xml',
// 			              reportFileName      : '**/report.html',
// 			              logFileName         : '**/log.html',
// 			              disableArchiveOutput: false,
// 			              passThreshold       : 50,
// 			              unstableThreshold   : 40,
// 			              otherFiles          : "**/*.png,**/*.jpg",
// 			            ]
// 		          	)
// 		        }
// 	  	}
	   success {  
             echo 'Build successfully executed'
         }  
       failure {
         mail to: 'ankit.kumar@infostride.com',
             subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
             body: "Build number ${env.BUILD_NUMBER} has been failed. Track the issues by visiting the url  ${env.BUILD_URL}"
	    }
    }
}
	


