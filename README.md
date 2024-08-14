# EC2 Chef Configuration for Nginx Deployment

This project shows how to use Chef to configure an EC2 instance for Nginx. It provides a step-by-step guide for setting up Chef, creating cookbooks, and deploying Nginx. This project automates server configuration and application deployment with Chef’s management tools.

This project demonstrates the process of using Chef to set up Nginx on an Amazon EC2 instance. The repository includes:

1. Chef Environment Setup: Commands for creating the project and cookbook directories.
2. Cookbook Creation: Instructions for generating and editing a cookbook to install and manage Nginx.
3. Recipe Execution: Steps to run the Chef recipe locally and verify Nginx installation.
4. Verification: Instructions for checking the Nginx version and accessing it via a web browser.

### EC2 - Chef Configuration

Comprehensive guide for configuring an EC2 instance using Chef to install and manage Nginx. Follow the steps below to set up the Chef environment, create a cookbook, and deploy Nginx on an EC2 instance.

#### 1. Create Project Folder

Initialize a new Chef repository with the following command:
```bash
chef generate repo myproject
```

Navigate to the project directory:
```bash
cd myproject
```

Change to the cookbooks directory:
```bash
cd cookbooks/
cd ..
```

#### 2. Create Cookbook

Generate a new cookbook for Nginx:
```bash
chef generate cookbook cookbooks/nginx
```

Navigate to the recipes directory within the Nginx cookbook:
```bash
cd cookbooks/nginx/recipes/
```

Edit the `default.rb` recipe file:
```bash
sudo nano default.rb
```

Paste the following code into `default.rb`:
```ruby
package 'nginx' do
  action :install
end

service 'nginx' do
  action [:enable, :start]
end
```

#### 3. Run Recipe

Execute the Chef recipe in local mode:
```bash
sudo chef-client --local-mode --runlist recipe[nginx::default]
```

#### 4. Verify Nginx Installation

Check the Nginx version to ensure it has been installed correctly:
```bash
nginx -v
```

#### 5. Access Nginx

Obtain the public IP address of your EC2 instance and open it in a web browser. Ensure that the inbound rule for port 80 is configured in the Security Group:
```
SG: Inbound rule - 80
http://instance-ip:80
```

### Nginx Service Management Commands

These commands are used to manage the Nginx service on a Linux system using `systemctl`, which is the system and service manager for Linux. 

1. **Stop the Nginx Service**
   ```bash
   sudo systemctl stop nginx
   ```
   This command stops the Nginx service. The service will be halted, and Nginx will no longer respond to requests until it is restarted.

2. **(Typo: Incorrect Command)**
   ```bash
   sudo systemctl startp nginx
   ```
   Note: This command contains a typo (`startp` should be `start`). It will not execute correctly. The correct command to start Nginx is:
   ```bash
   sudo systemctl start nginx
   ```

3. **Start the Nginx Service**
   ```bash
   sudo systemctl start nginx
   ```
   This command starts the Nginx service. The service will begin running and will start responding to requests.

4. **Check the Status of the Nginx Service**
   ```bash
   sudo systemctl status nginx
   ```
   This command displays the current status of the Nginx service, including whether it is active (running), inactive (stopped), or in a failed state. It also provides additional information such as the last few log entries.

---

Make sure to use `systemctl start nginx` to properly start the service, and correct any typos to ensure commands execute as intended.
