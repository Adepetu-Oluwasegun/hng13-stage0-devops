## Project Overview
This project involves provisioning a Linux server on AWS, installing a web server (Nginx), and deploying a simple HTML landing page to demonstrate my skills., accessible via the public IP of the server.

## Table of Contents
- [Provisioning the Server](#provisioning-the-server)
- [Installing Nginx Web Server](#installing-nginx-web-server)
- [HTML Page Deployment](#html-page-deployment)
- [Networking and Security](#networking-and-security)
- [Testing the Web Page](#testing-the-web-page)
- [Public IP Address](#public-ip-address)
- [Screenshot](#screenshot)

---

## Provisioning the Server
1. **Log in to AWS:**
   - Access [AWS Console](https://aws.amazon.com/console/).
   - Navigate to EC2 and launch a new instance.
2. **Choose AMI:**
   - Select Ubuntu 24.04 LTS.
3. **Instance Type:**
   - Choose t3.micro (free tier eligible).
4. **Configure Instance:**
   - Add necessary tags (Name: ).
   - See to it that SSH key pair is created and downloaded.
5. **Security Group:**
   - Allow inbound traffic on ports 22 (SSH), 80 (HTTP)
6. **Launch Instance:**
   - Download the private key (e.g., `hng.pem`) for SSH access.

---

## Installing Nginx Web Server
1. **Connect to the Instance:**
   ```bash
   ssh -i hng.pem ubuntu@<your-public-ip>
   ```
2. **Update the Server:**
   ```bash
   sudo apt get update 
   ```
3. **Install Nginx:**
   ```bash
   sudo apt-get install nginx -y
   ```
4. **Start Nginx:**
   ```bash
   sudo systemctl start nginx
   ```
5. **Enable Nginx to Start on Boot:**
   ```bash
   sudo systemctl enable nginx
   ```

---

## HTML Page Deployment
1. **Go over to the Web Root:**
   ```bash
   cd /var/www/html
   ```
2. **Create an HTML Page:**
   ```bash
   sudo nano index.html
   ```
3. **Add HTML Content:**
   ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>HNG13 DevOps Stage 0</title>
   <style>
    body {
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      color: white;
    }
    .container {
      text-align: center;
      padding: 2rem;
      background: rgba(255, 255, 255, 0.1);
      border-radius: 10px;
      backdrop-filter: blur(10px);
    }
    h1 { margin-bottom: 1rem; }
    .timestamp { font-size: 0.9em; opacity: 0.8; }
   </style>
    </head>
    <body>
      <div class="container">
        <h1>Welcome to DevOps Stage 0 - Oluwasegun Adepetu/@Adepetu Oluwasegun</h1>
        <p>Successfully deployed on AWS</p>
        <p class="timestamp">Deployed: 17/10/2025</p>
    </div>
    </body>
    </html>
   ```
4. **Save and Exit:**
   ```bash
   CTRL + O, ENTER, CTRL + X
   ```
5. **Adjust Permissions:**
   ```bash
   sudo chmod 755 /var/www/html/index.html
   ```

---

## Networking and Security
1. **Security Group Configuration:**
   - Allow HTTP (port 80).
   - Make sure SSH (port 22) is restricted to your IP for security.
2. **Verify Nginx Configuration:**
   ```bash
   sudo systemctl status nginx
   ```
3. **Restart Nginx if Needed:**
   ```bash
   sudo systemctl restart nginx
   ```

---

## Testing the Web Page
1. **Access the Web Page:**
   - Open a browser and visit `http://98.81.211.215/`.
2. **Verify HTML Page Displays Properly.**

---

## Public IP Address
`http://98.81.211.215/`
