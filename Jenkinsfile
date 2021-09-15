pipeline {
    agent {
        docker {
            image 'node:lts-buster-slim' 
            args '-p 3000:3000' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }
    }
}

/* 
    This image parameter (of the agent section’s docker parameter) downloads the node:lts-buster-slim Docker image (if it’s not already available on your machine) and runs this image as a separate container. This means that:
    You’ll have separate Jenkins and Node containers running locally in Docker.

    The Node container becomes the agent that Jenkins uses to run your Pipeline project. However, this container is short-lived - its lifespan is only that of the duration of your Pipeline’s execution.

    This args parameter makes the Node container (temporarily) accessible through port 3000. The significance of this is explained in the jenkins/scripts/deliver.sh file of your cloned repository, and is covered in a subsequent section of this tutorial.
    Defines a stage (directive) called Build that appears on the Jenkins UI.
    This sh step (of the steps section) executes the npm command to ensure that all dependencies required to run your application have been downloaded to the node_modules workspace directory (within the /var/jenkins_home/workspace/simple-node-js-react-npm-app directory in the Jenkins container). 
*/