pipeline {
    agent any
    stages{
        stage("deploy"){
            steps{
                echo "In the deploy stage"
                bat "kubectl version"
            }
        }
    }
}