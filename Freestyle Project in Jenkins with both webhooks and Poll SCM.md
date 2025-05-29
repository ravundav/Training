## Jenkins Freestyle Project with Webhooks and Poll SCM

### 1. Create a Freestyle Project
- Go to your Jenkins dashboard.
- Click **New Item**.
- Enter a name and select **Freestyle project**.
- Click **OK**.

### 2. Configure Source Code Management (SCM)
- In the project configuration, scroll to **Source Code Management**.
- Select **Git** (or your SCM).
- Enter your repository URL and credentials if needed.

### 3. Set Up Poll SCM
- Scroll to **Build Triggers**.
- Check **Poll SCM**.
- Enter a schedule (e.g., `H/5 * * * *` for every 5 minutes).

<img width="1357" alt="image" src="https://github.com/user-attachments/assets/f46c0a6f-7c14-4c15-9f26-8703f158c777" />

### 4. Set Up Webhooks (GitHub Example)
- Go to your repository on GitHub.
- Click **Settings** > **Webhooks** > **Add webhook**.
- Set the **Payload URL** to:  
  `http://<your-jenkins-server>/github-webhook/`
- Set **Content type** to `application/json`.
- Choose which events to trigger the webhook (usually "Just the push event").
- Click **Add webhook**.

<img width="1076" alt="image" src="https://github.com/user-attachments/assets/0159d852-cf77-462a-87a8-21c994b4c33d" />

<img width="1159" alt="image" src="https://github.com/user-attachments/assets/1f050d84-9d2c-4059-abe4-093ddd2bc4f2" />


### 5. Enable GitHub Hook Trigger in Jenkins
- In **Build Triggers**, check **GitHub hook trigger for GITScm polling**.

### 6. Save and Build
- Click **Save**.
- Now, Jenkins will build when:
  - A webhook is received (e.g., on push)
  - The Poll SCM schedule detects changes

---

**Note:**  
- Make sure your Jenkins server is accessible from GitHub for webhooks to work.
- You can use both triggers together; Jenkins will build on either event.
