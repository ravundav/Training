## Pipeline Overview

This project uses three separate pipelines for **Clone**, **Build**, and **Deploy** stages. Each pipeline is responsible for a specific part of the CI/CD process.

### 1. Clone Pipeline

- **Purpose:** Clones the repository from the source control system.
- **Trigger:** Manual or on code push.
- **Output:** Latest source code checked out to the workspace.

### 2. Build Pipeline

- **Purpose:** Installs dependencies and builds the application.
- **Trigger:** After successful clone.
- **Output:** Build artifacts ready for deployment.

### 3. Deploy Pipeline

- **Purpose:** Deploys the built artifacts to the target environment.
- **Trigger:** After successful build.
- **Output:** Application deployed and running.

## Example Jenkinsfiles

**Clone Pipeline**
```groovy
pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                checkout scm
            }
        }
    }
}
```

<img width="1135" alt="image" src="https://github.com/user-attachments/assets/44b95219-09c8-42b9-a74f-06f56a7919bd" />

<img width="1176" alt="image" src="https://github.com/user-attachments/assets/fa8d94ea-4fce-4704-894a-1de76bffdaa6" />



**Build Pipeline**
```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }
    }
}
```

<img width="1342" alt="image" src="https://github.com/user-attachments/assets/de82a207-2a6f-4c97-8340-3c5652bb536c" />

<img width="1308" alt="image" src="https://github.com/user-attachments/assets/3b9f350a-bc82-4802-b23e-9fa9a859aa06" />


**Deploy Pipeline**
```groovy
pipeline {
    agent any
    stages {
        stage('Deploy') {
            steps {
                sh './deploy.sh'
            }
        }
    }
}
```

<img width="1364" alt="image" src="https://github.com/user-attachments/assets/0e038719-8769-4e44-a318-d7151c8b91c1" />


## How to Use

1. **Run the Clone pipeline** to fetch the latest code.
2. **Run the Build pipeline** to compile and package the application.
3. **Run the Deploy pipeline** to deploy the application to your environment.

You can configure triggers and artifact sharing between pipelines as needed for your CI/CD workflow.

## Build Pipeline View

**You need to install Build pipeline Plugin**

<img width="1324" alt="image" src="https://github.com/user-attachments/assets/7171f813-c902-4fcd-9e88-80839016a01e" />

<img width="1427" alt="image" src="https://github.com/user-attachments/assets/f6ec2c7c-2bf5-45e0-bd64-1eb30391af8d" />


| Stage         | Status   | Description                  |
|---------------|----------|------------------------------|
| Checkout Code | ✅ Passed | Clone repository from source |
| Install Deps  | ✅ Passed | Install project dependencies |
| Lint          | ✅ Passed | Run code linting             |
| Test          | ✅ Passed | Run unit/integration tests   |
| Build         | ✅ Passed | Build application artifacts  |
| Archive Artifacts | ✅ Passed | Save build outputs         |

**Sample Visualization:**

```
[Checkout Code] → [Install Deps] → [Lint] → [Test] → [Build] → [Archive Artifacts]
        ✅               ✅           ✅         ✅         ✅              ✅
```

- Each stage is executed in order.
- Status indicators (✅/❌) show pass/fail.
- Artifacts from the build are archived for deployment.
