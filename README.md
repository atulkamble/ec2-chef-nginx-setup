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
