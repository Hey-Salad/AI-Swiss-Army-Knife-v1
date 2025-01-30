
<img src="https://raw.githubusercontent.com/Hey-Salad/.github/refs/heads/main/HeySalad%20Logo%20%2B%20Tagline%20Black.svg" alt="HeySalad Logo" width="400"/>

  ## Enterprise-Grade DeepSeek Implementation on GCP         
                                                              
=============================================================== 
 
 ## 🚀 Step-by-Step Guide to Deploy DeepSeek using Open WebUI on Google Cloud Platform
 
This README provides a detailed walkthrough on setting up an enterprise-grade 
implementation of DeepSeek, a powerful AI model, using Open WebUI on Google Cloud 
Platform (GCP). The setup ensures high availability, scalability, and security for
mission-critical applications.

Test -> https://chat.heysalad.app/
 
## 📋  Table of Contents
- [Prerequisites](#prerequisites)
- [Step 1: Provision GCP Resources](#step-1-provision-gcp-resources)
- [Step 2: Set Up the Instance](#step-2-set-up-the-instance)
- [Step 3: Deploy Open WebUI](#step-3-deploy-open-webui)
- [Step 4: Configure SSL/TLS (Optional)](#step-4-configure-ssltls-optional)
- [Step 5: Set Up DNS and Firewall Rules](#step-5-set-up-dns-and-firewall-rules)
- [Step 6: Access and Configure Open WebUI](#step-6-access-and-configure-open-webui)
- [Troubleshooting](#troubleshooting)
- [Conclusion](#conclusion)
 
## 🔧 Prerequisites
- A Google Cloud Platform account with billing enabled
- Basic knowledge of GCP and command-line interface (CLI)
- Familiarity with Docker and containerization concepts
 
##  🖥️ Step 1: Provision GCP Resources
1. Create a new GCP project or select an existing one.
2. Enable the necessary APIs:
- Compute Engine API
- Container Registry API
3. Create a GCP instance with the following specifications:
- Machine type: Depending on your requirements (e.g., n1-standard-4)
- GPU: NVIDIA Tesla P100 or similar
- Boot disk: Deep Learning VM image (e.g., Deep Learning on Linux)
- Firewall: Allow HTTP and HTTPS traffic
 
## 🔩  Step 2: Set Up the Instance
1. Connect to the GCP instance using SSH.
2. Update the system packages:
     ```
     sudo apt update && sudo apt upgrade -y

   ```
3. Install the NVIDIA driver:
   ```
   sudo /opt/deeplearning/install-driver.sh
   ```
4. Install Docker and Docker Compose:
   ```bash
     sudo apt install docker.io docker-compose -y
   ```
5. Add your user to the docker group:
```
  sudo usermod -aG docker $USER
```
   Log out and log back in for the changes to take effect.
 
## 🐳  Step 3: Deploy Open WebUI
  1. Clone the Open WebUI repository:
`bash
  git clone https://github.com/open-webui/open-webui.git
  cd open-webui
`
2. Create a Docker volume for persistent storage:
   ```bash
   docker volume create open-webui  
   ```
3. Create a `.env\` file in the project root and configure the necessary environment variables:
   ```bash
   ## Example .env file
   OLLAMA_API_BASE_URL=http://localhost:11434
   DATABASE_URL=sqlite:////app/backend/data/webui.db
   WEBUI_AUTH=true
   WEBUI_SECRET_KEY=your_secret_key
     ```
4. Build and start the Open WebUI container:
    ```bash
    docker-compose up -d
     ```

 ## 🔒 Step 4: Configure SSL/TLS (Optional)
1. Install Nginx and Certbot:
     ```bash
     sudo apt install nginx certbot python3-certbot-nginx -y
     ```
2. Configure Nginx as a reverse proxy for Open WebUI.
3. Obtain SSL certificates using Certbot:
     ```bash
     sudo certbot --nginx -d your_domain.com
     ```
 
  ## 🌐  Step 5: Set Up DNS and Firewall Rules
1. Configure your domain's DNS settings to point to the GCP instance's public IP address.
2. Create firewall rules in GCP to allow incoming traffic on ports 80 (HTTP) and 443 (HTTPS).
 
 ## 🎉  Step 6: Access and Configure Open WebUI
1. Access the Open WebUI interface using your domain or the instance's public IP address.
2. Follow the on-screen instructions to create an admin account and log in.
3. Set up and configure the DeepSeek model according to the Open WebUI documentation.

## 🤔 Troubleshooting
- If you encounter issues with the Open WebUI interface, check the Docker container logs:
    ```
    docker-compose logs -f
    ```
 - Verify that the firewall rules are correctly configured and the instance is reachable.
 - Ensure that the SSL/TLS certificates are properly installed and configured.
 - Double-check the environment variables in the \`.env\` file.
 
 ## 🎊  Conclusion
By following this step-by-step guide, you can deploy an enterprise-grade implementation 
of DeepSeek using Open WebUI on Google Cloud Platform. This setup ensures a reliable, 
scalable, and secure solution for your AI workloads.
 
   For more information and advanced configurations, refer to the official Open WebUI and
  Google Cloud Platform documentation.
 
  ---
 
##  📜 Legal
 
### Trademark Notice
HeySalad® (UK Trademark Registration No. UK00004063403) is a registered trademark of SALADHR TECHNOLOGY LTD, headquartered at Plexal, Here East, Queen Elizabeth Olympic Park, London, England, E20 3BS (Company Number: 14979493).
 
  ### Legal Disclaimer
The information provided above is for general informational purposes only and does not constitute legal or professional advice. Any use of the HeySalad® name, trademark, or related branding without the express written permission of SALADHR TECHNOLOGY LTD is strictly prohibited. SALADHR TECHNOLOGY LTD disclaims all liability for any losses or damages arising from reliance on or use of the information provided herein.
 
   ## 📜 License
  This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
 
 ##  ❤️  Support
  If you find this guide helpful, consider buying us a coffee!
  <a href="https://www.buymeacoffee.com/heysalad" target="_blank"><img src="https://img.buymeacoffee.com/button-api/?text=Buy me a coffee&emoji=&slug=heysalad&button_colour=FFDD00&font_colour=000000&font_family=Cookie&outline_colour=000000&coffee_colour=ffffff" alt="Buy Me A Coffee" width="200"/></a>
 
## 🤝  Contributing
 We welcome contributions! If you have any suggestions, improvements, or bug fixes, please
   open an issue or submit a pull request on the [GitHub repository](https://github.com/Hey-Salad/AI-Swiss-Army-Knife-v1.git).
 
## 📧  Contact
 For any questions or inquiries, please reach out to us at:
 - Website: [heysalad.app](https://heysalad.app)
 - Email: peter@heysalad.io

© 2025 SALADHR TECHNOLOGY LTD. All rights reserved.

🍽️ Made with ❤️ by HeySalad
