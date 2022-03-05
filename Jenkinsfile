pipeline {
    agent any
    stages{
        stage("deploy"){
            steps{
                echo "In the deploy stage"
                bat "kubectl version"
                bat "if exist mini-ws (rmdir /S /Q mini-ws)"
                bat "git clone https://github.com/colintran/mini-ws.git && cd ./mini-ws && git checkout master && cd .."
                bat "docker image build -t trand/miniws ./mini-ws"
                bat "kubectl apply -f myws.deployment.yaml"
                /*
                TODO: Monitor until all pod status are Running
                */
                echo "Deployment done."
            }
        }
    }
}