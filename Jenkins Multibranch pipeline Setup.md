## Jenkins Pipeline Setup

1. In the Jenkins dashboard, click on **New Item**.
2. Enter an item name (e.g., `My Sample Pipeline`).
3. Select **Multibranch Pipeline** as the project type.
4. Click **OK**.
5. You will now see the configuration page for your new Multibranch Pipeline project.

<img width="681" alt="image" src="https://github.com/user-attachments/assets/a2ce96d0-8cd8-4f89-a63e-c49f8b66f204" />

1. **Display Name**: Enter a name of your choice for the pipeline.
2. Under **Branch Sources**, select **Git**.
3. Provide your project repository URL.
4. Click **Save** to apply the configuration.
<img width="889" alt="image" src="https://github.com/user-attachments/assets/b592e4cd-c5b6-4f39-8695-47fb95f9a7c1" />

## Setting Up SSH Key Authentication Between Jenkins and Tomcat Server

1. **Generate an SSH key on the Jenkins server:**

   ```sh
   ssh-keygen -t rsa -b 4096 -C "jenkins@yourdomain.com"
   ```
   - Press Enter to accept the default file location.
   - Set a passphrase if desired.

2. **Copy the Jenkins public SSH key to the Tomcat server:**

   ```sh
   ssh-copy-id user@tomcat-server
   ```
   - Replace `user` with your Tomcat server username.
   - Replace `tomcat-server` with your Tomcat server's address.

   This allows Jenkins to connect to the Tomcat server via SSH without a password.

---

## Installing Maven and Java on Jenkins Server

```sh
sudo apt-get update
sudo apt-get install openjdk-17-jdk
sudo apt-get install maven
```
<img width="1071" alt="image" src="https://github.com/user-attachments/assets/01ac21c1-9090-440f-bdf9-dd2ee3762dce" />

<img width="886" alt="image" src="https://github.com/user-attachments/assets/094d8313-1497-4944-9b9a-d4afaa32b9d9" />

<img width="359" alt="image" src="https://github.com/user-attachments/assets/a33a2f34-4f9b-43cc-ba53-a81501ff114f" />

## You need to replace the highlighted section with the IP address of your web application server.
<img width="706" alt="image" src="https://github.com/user-attachments/assets/7ef64a4b-d418-4f2a-9e69-665a7c9bc4f6" />

## Click on build now
<img width="665" alt="image" src="https://github.com/user-attachments/assets/28cf030c-33a9-480c-b1d0-094e47c56c38" />

## How to Check if the Build is Successful

1. After running your build command (e.g., `npm run build`, `mvn clean install`, etc.), open the **Console Output** (or Terminal).
2. Look for messages such as **"BUILD SUCCESSFUL"** or **"BUILD FAILED"**.
   - If you see **"BUILD SUCCESSFUL"** or a similar message, the build was successful.
   - If you see **"BUILD FAILED"** or any error messages, the build was not successful.
3. Always review the Console Output to confirm the build status.
<img width="538" alt="image" src="https://github.com/user-attachments/assets/b25510a7-a551-454d-863c-7030cef91112" />

## Checking Jenkins Pipeline for a New Branch

1. **Create a new branch** in your Git repository:
   ```sh
   git checkout -b your-feature-branch
   git push origin your-feature-branch
   ```

2. **Refresh your Jenkins page**.  
   Jenkins should automatically detect the new branch and create a corresponding pipeline.

3. **Check the Jenkins dashboard** to see if a new pipeline appears for your branch and observe its build status.  
   *You should see the new pipeline without needing to trigger any manual builds.*
