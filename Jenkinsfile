pipeline {
    agent any
    environment { scannerHome = tool 'central' }
    stages {
        stage("SonarQube Scanning") {
            steps {
                script { 
                    if (env.CHANGE_ID) { 
                        withSonarQubeEnv("sonarqube.devops.vtxdev.net") { 
                            bat "\"${scannerHome}\\bin\\sonar-scanner.bat\" -Dsonar.projectKey=prdecospub -Dsonar.pullrequest.key=${CHANGE_ID} -Dsonar.pullrequest.branch=${GIT_BRANCH}"; 
                            } 
                        }
                    else { 
                        withSonarQubeEnv("sonarqube.devops.vtxdev.net") { 
                            bat "\"${scannerHome}\\bin\\sonar-scanner.bat\" -Dsonar.projectKey=prdecospub -Dsonar.branch.name=${GIT_BRANCH}"; 
                            } 
                        }
                }
            }
        }
    }
}
