pipeline {
	agent any
	
	//tools {
        // maven "maven3"
       // jfrog 'jfrog-cli'
    //}
	
    // environment {

    // }
	
    stages {
        // stage('Testing') {
        //     steps {
        //         withEnv(["JFROG_BINARY_PATH=${tool 'jfrog-cli'}"]) {
        //              // Show the installed version of JFrog CLI.
        //             jf '-v'

        //             // Show the configured JFrog Platform instances.
        //             jf 'c show'

        //             // Ping Artifactory.
        //             jf 'rt ping'
        //         }
               
        //     }
        // }
        stage('BUILD'){
            steps {
                sh 'mvn clean install -DskipTests'
            }
        }
    }
}