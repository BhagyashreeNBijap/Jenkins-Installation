## 🚀 Jenkins Installation on Amazon Linux 2 (EC2) with MobaXterm

### ✅ Step 1: Launch an EC2 Instance

* **AMI**: Amazon Linux 2
* **Instance Type**: `t2.micro`
* **Security Group**: Allow **all traffic** (for testing/demo purposes)
* Launch the instance.

----------------------------------------------------------------------------------------------------------------

### 💻 Step 2: Connect Using MobaXterm

1. Open **MobaXterm**.
2. Connect to your EC2 instance using your `.pem` key file:

   ssh -i path_to_key.pem ec2-user@<your-ec2-public-ip>
  
3. Switch to the root user:

   sudo su -

--------------------------------------------------------------------------------------------------------------------

### ☕ Step 3: Install Java

Install Java 17 using the following command:

yum install java-17* -y


--------------------------------------------------------------------------------------------------------------------

### 🔽 Step 4: Download and Configure Jenkins Repository

1. Open a browser and go to the [Jenkins Downloads Page](https://www.jenkins.io/download/).
2. Select **Red Hat / CentOS** under **Linux** > **Long-Term Support (LTS)**.
3. Copy and paste the following commands into your terminal:


   sudo wget -O /etc/yum.repos.d/jenkins.repo \
     https://pkg.jenkins.io/redhat-stable/jenkins.repo
   sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
   sudo yum upgrade -y
   sudo yum install fontconfig java-21-openjdk -y
   sudo yum install jenkins -y
   sudo systemctl daemon-reload
 

--------------------------------------------------------------------------------------------------------------------

### ▶️ Step 5: Start Jenkins

Start the Jenkins service:

systemctl start jenkins

--------------------------------------------------------------------------------------------------------------------

### 🌐 Step 6: Access Jenkins in Browser

1. Open your browser and enter:

  public ip of your instance with port no. of 8080

 Eg: 3.110.107.72:8080

2. If the page doesn't load, ensure port **8080** is allowed in the EC2 security group.


--------------------------------------------------------------------------------------------------------------------

### 🔐 Step 7: Unlock Jenkins

1. In your terminal, get the initial admin password:


   sudo cat /var/lib/jenkins/secrets/initialAdminPassword
 
2. Copy and paste the password into the Jenkins setup page in your browser.


--------------------------------------------------------------------------------------------------------------------

### 🧩 Step 8: Jenkins Setup Wizard

* Select **Install Suggested Plugins**.
* Create the first admin user:

  * **Username**: admin
  * **Password**: your password
  * **Email**: your email
* Save and finish the setup.


✅ **Jenkins is now installed and ready to use!**

