pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "maven"
    }
    
//     parameters{
//         string(name: 'Company', defaultValue: 'PS', description: 'Enter the name of your Company')
//         booleanParam(name: 'Run Test Cases', defaultValue: true, description: 'Do you want to run test cases while building?')
//         choice(name: 'env', choices: ['DEV', 'PROD'], description: 'Specify the build environment') 
//     }

    stages {
        stage('Build') {
            steps {
                
                git branch:"jenkins-works", url:'https://github.com/vsushruth/sapient-freshers-2021-jun-asde.git'

                // Run Maven on a Unix agent.
                //sh "mvn -Dmaven.test.failure.ignore=true clean package"
                sh "mvn clean install"
                bat "docker image build -t java-app ."
                bat "docker run java-app:latest"

                // To run Maven on a Windows agent, use
//                 bat "mvn clean install"
//                 bat "docker image build -t java-app ."
//                 bat "docker run java-app:latest"
            }

        }
    }
}
