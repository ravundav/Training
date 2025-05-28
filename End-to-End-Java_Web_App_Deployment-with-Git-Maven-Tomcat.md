# End-to-End Java Web App Deployment with Git, Maven, and Tomcat

This guide walks you through deploying a Java web application using Git, Maven, and Tomcat on AWS EC2 instances.

---

## 1. Git Setup on EC2 (Build Server)

1. **Create a GitHub account** (if you don’t have one).
2. **On your EC2 instance:**
   ```bash
   mkdir git
   cd git
   ```
3. **Clone your training repository:**
   ```bash
   git clone https://github.com/<your-username>/training.git
   ```
4. **Clone the instructor’s repository:**
   ```bash
   git clone https://github.com/prasad-srtech/exp_an.git
   ```
5. **Check the directories:**
   ```bash
   ls
   # Output: exp_an  training
   ```
6. **Copy all content from exp_an to your training folder:**
   ```bash
   cp -pr exp_an/* training/
   ```
7. **Navigate to the training directory:**
   ```bash
   cd training
   ```
8. **Add, commit, and push the changes:**
   ```bash
   git add .
   git commit -m "Added training files"
   git push
   # Enter your GitHub username and personal access token when prompted
   ```
9. **Verify:**  
   Check your GitHub repo in the browser to confirm files are uploaded.

---

## 2. Build with Maven

1. **Install Maven:**
   ```bash
   sudo apt-get update
   sudo apt-get install maven
   ```
2. **Navigate to your repo folder (where `pom.xml` is located):**
   ```bash
   cd ~/git/training
   ```
3. **Build the project:**
   ```bash
   mvn install
   ```
4. **Check the build output:**
   ```bash
   ls
   # You should see: Jenkinsfile  README.md  numbers.java  pom.xml  src  target
   ls target/
   # You should see: exp_an.war and other build artifacts
   ```

---

## 3. Deployment Setup (Deployment Server)

1. **Create and configure a new EC2 instance for deployment.**
2. **On the deployment EC2 instance:**
   ```bash
   sudo apt-get update
   sudo apt-get install openjdk-17-jdk
   ```
3. **Install Tomcat:**
   ```bash
   mkdir distros
   chmod -R 777 distros
   cd distros
   wget https://dlcdn.apache.org/tomcat/tomcat-10/v10.1.41/bin/apache-tomcat-10.1.41.tar.gz
   tar -zxvf apache-tomcat-10.1.41.tar.gz
   rm -rf apache-tomcat-10.1.41.tar.gz
   ```

---

## 4. Copy WAR File from Build to Deployment Server

1. **On the build server, generate an SSH key (if not already done):**
   ```bash
   ssh-keygen
   cat ~/.ssh/id_ed25519.pub
   ```
2. **On the deployment server, add the build server’s public key to `~/.ssh/authorized_keys`:**
   - Paste the contents of `id_ed25519.pub` into `~/.ssh/authorized_keys`
3. **Test SSH connectivity from build to deployment server:**
   ```bash
   ssh <deployment-server-ip>
   ```
4. **Copy the WAR file to the deployment server:**
   ```bash
   scp target/exp_an.war root@<deployment-server-ip>:/root/distros/apache-tomcat-10.1.41/webapps/
   ```
5. **On the deployment server, verify the WAR file is copied:**
   ```bash
   ls /root/distros/apache-tomcat-10.1.41/webapps/
   ```

---

## 5. Start/Stop Tomcat

- **Start Tomcat:**
  ```bash
  sh /root/distros/apache-tomcat-10.1.41/bin/startup.sh
  ```
- **Stop Tomcat:**
  ```bash
  sh /root/distros/apache-tomcat-10.1.41/bin/shutdown.sh
  ```

---

## 6. Access the Application

- By default, Tomcat runs on port 8080.
- Make sure to allow inbound traffic on port 8080 in your EC2 security group to access the web app from your browser.

---

**Note:**
- Use `sudo` as needed for permissions.
- Replace `<your-username>` and `<deployment-server-ip>` with your actual values.
