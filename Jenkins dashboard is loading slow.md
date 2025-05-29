## Updating Jenkins IP Address in Manage Jenkins

If your Jenkins dashboard is loading slowly and you need to update the IP address, follow these steps:

1. **Open Jenkins Dashboard**  
   Go to your Jenkins URL in your browser.

2. **Navigate to Manage Jenkins**  
   Click on **Manage Jenkins** from the left sidebar.

3. **Go to Configure System**  
   Click on **Configure System**.

4. **Update Jenkins URL**  
   - Find the field labeled **Jenkins URL** (sometimes called **Jenkins Location**).
   - Update the URL to use the new IP address (e.g., `http://NEW_IP_ADDRESS:8080/`).

5. **Save Changes**  
   Scroll down and click **Save**.

6. **Restart Jenkins (Optional)**  
   For some changes to take effect, you may need to restart Jenkins.  
   You can do this from the terminal:
   ```sh
   sudo systemctl restart jenkins
   ```
   or
   ```sh
   sudo service jenkins restart
   ```

**Note:**  
- If Jenkins is behind a proxy or load balancer, ensure the proxy settings are updated as well.
- Slow dashboard loading can also be caused by plugins, system resources, or network issues unrelated to the IP address.
  
<img width="996" alt="image" src="https://github.com/user-attachments/assets/28c6fcef-6850-4b9d-b7d5-ac190dc1530d" />

<img width="818" alt="image" src="https://github.com/user-attachments/assets/fef3664e-338b-46ed-9c1b-175af35383a6" />

