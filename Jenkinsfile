@Library('Test-Shared-Library') _

// def globalvar

pipeline {
    agent any
    
    parameters {
        string(name: 'repoUrl', defaultValue: 'https://github.com/Shruthika-Ravi/Maven-project.git', description: 'Repo Name')
        choice(name: 'branchName', choices: ['main', 'test'], description: 'Choose Branch Name')
    }
    
    stages {
        
        stage('Git Checkout') {
            steps {
            gitCheckout(
                branch: "${branchName}",
                url: "${repoUrl}"
            )
            }
    }
        
        stage (Build and Package') {
  steps {
    script {
      //begin common code 
      if (fileExists()) {
        def readcounter =    readFile(file: 'version.txt')
        readcounter = readcounter.toInteger() +1
        def version= "Version" + readcounter
        println(version)
        bat 'mvn package -Dartifactversion=' + "${version}"
        writeFile(file: 'version.txt',    text:readcounter.toString())
      } //if condition
      else {
        currentBuild.result = "FAILURE" 
      } //else condition
//end common code
    } //script
    echo "Build and Package Completed" 
  } //steps
} //stage
        
    } 
}
