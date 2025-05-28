## Jenkins Freestyle Project

This project uses a Jenkins Freestyle Project for continuous integration.

### How to Set Up

1. **Open Jenkins Dashboard.**
2. Click **"New Item"**.
3. Enter a project name (e.g., `my-freestyle-project`).
4. Select **"Freestyle project"** and click **OK**.
5. In **Source Code Management**, select **Git** and enter your repository URL.
6. In **Build Triggers**, choose how you want the build to be triggered (e.g., Poll SCM, Build periodically).
7. In **Build**, add a build step (e.g., "Execute shell") and enter your build commands, for example:
    ```sh
    echo "Building the project..."
    # Add your build commands here
    ```
8. In **Post-build Actions**, add any actions you need (e.g., archive artifacts, email notifications).
9. Click **Save**.

### Usage

- To build manually, click **"Build Now"** in Jenkins.
- View build status and logs in the Jenkins UI.

For more details, see the [Jenkins Freestyle Project documentation](https://www.jenkins.io/doc/book/pipeline/getting-started/#freestyle-projects).

<img width="1261" alt="image" src="https://github.com/user-attachments/assets/bbf0f130-bf0a-4e33-a4fe-544482127e61" />
<img width="808" alt="image" src="https://github.com/user-attachments/assets/35964698-ea2c-4158-a39c-7e325b89b74c" />
<img width="497" alt="image" src="https://github.com/user-attachments/assets/f3c3ca1b-1299-4091-8423-6b0ed9917db9" />
<img width="1213" alt="image" src="https://github.com/user-attachments/assets/9a5bd30a-010e-41d3-be5f-695a18c4642c" />
<img width="595" alt="image" src="https://github.com/user-attachments/assets/25e2a58c-5282-40ac-8501-3c3685aa67ac" />
<img width="984" alt="image" src="https://github.com/user-attachments/assets/71c188f7-43a0-4d7b-87e8-b40136c9c331" />
