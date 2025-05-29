# Pipeline Project

This project uses a Jenkins Pipeline to automate building, testing, and deploying the application.

## Jenkins Pipeline

The pipeline is defined in the `Jenkinsfile` at the root of this repository. It consists of the following stages:

1. **Checkout**: Retrieves the latest code from the repository.
2. **Build**: Installs dependencies and builds the application.
3. **Test**: Runs automated tests to ensure code quality.
4. **Deploy**: Deploys the application to the target environment (if tests pass).

## Running the Pipeline

To run the pipeline:

1. Ensure Jenkins is installed and running.
2. Create a new Pipeline job in Jenkins.
3. Point the job to this repository.
4. The pipeline will execute automatically based on the `Jenkinsfile`.

## Jenkinsfile Example

```groovy
pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'echo "Building..."'
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Running tests..."'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo "Deploying..."'
            }
        }
    }
}
```

## Requirements

- Jenkins 2.x or later
- Appropriate build and test tools installed on the Jenkins agent

<img width="1110" alt="image" src="https://github.com/user-attachments/assets/1a1a3533-abfb-4d24-b8e1-88a36050ee4a" />
