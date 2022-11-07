@Library('Test-Shared-Library') _

def readcounter = readFile(file: 'version.txt')
readcounter=readcounter.toInteger() +1
def version= "Version" + readcounter
println(version)

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
    }
    
    stage('Git Tag') {
        steps {
            gitTag()
        }
    }
    
}
