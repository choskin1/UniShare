<h1 align="center" style="color: #2E8B57;">📚 UniShare: Connect, Collaborate, Conquer Your Studies 📚</h1>

<p align="center">
  Welcome to <b style="color: #4682B4;">UniShare</b>, the ultimate platform designed for students who believe in the power of collaborative learning. Whether you're looking to join a study group, share essential files, or dive into a video conference to discuss that challenging topic, UniShare has got you covered.
</p>

## 🌟 Features:
- **📖 Join or Create Study Groups:** Find like-minded peers to tackle subjects together.
- **📁 File Sharing:** Easily share notes, assignments, and resources with group members.
- **📹 Video Conferencing:** Dive into real-time discussions and study sessions.
- **🔒 Secure & Private:** Your data is protected, and group interactions remain exclusive to members.

<p align="center" style="color: #8B4513;">
  With UniShare, you're not just studying; you're building a community of learners. Dive in and discover the future of collaborative education!
</p>


## Table of Contents
1. [Prerequisites](#prerequisites)
2. [Installation & Setup](#installation--setup)
3. [Usage](#usage)
4. [Application Design & Architecture](#application-design--architecture)
5. [Cloud Deployment](#cloud-deployment)
6. [Testing](#testing)
7. [Contributing](#contributing)
8. [License](#license)
9. [Acknowledgments](#acknowledgments)

## Prerequisites

Before you begin, ensure you have met the following requirements:

- **Amazon Web Services (AWS) Account:** The application is currently deployed using AWS services, including EC2, S3, and RDS. If you wish to modify or redeploy the application, you'll need an AWS account. Sign up [here](https://aws.amazon.com/).

- **Amazon Academy Learner Lab Credentials:** Access to the current deployment is through Amazon Academy Learner Lab credentials. Ensure you have these credentials handy.

- **Git:** To clone and manage the project repository.

- **Basic Knowledge of Cloud Services:** Familiarity with AWS services such as EC2, S3, and RDS will be beneficial.

- **Internet Connection:** To access cloud services and deploy the application.


## Installation & Setup

### 1. Setting up the EC2 for Web Server

1. **Launch an EC2 instance** on AWS and ensure it's running.
2. **SSH into the EC2 instance** using your preferred terminal or SSH client:
   ```bash
   ssh -i "your-key-pair.pem" ec2-user@your-ec2-instance-ip
3. **Clone the UniShare repository**:
   ```bash
   git clone https://github.com/choskin1/UniShare.git
4. **Navigate to the cloned repository** and run the frontend startup script:
   ```bash
   cd UniShare
   ./setup-frontend.sh
5. This will start the main Python application and create a server operating on port `5001`.

### 2. Setting up the RDS for Database

1. **Launch an RDS instance** on AWS:
   - Navigate to the RDS service in the AWS Management Console.
   - Choose the database engine (e.g., MySQL).
   - Configure the instance specifications, security groups, and other settings as needed.
   - Launch the RDS instance and note down the endpoint.
2. **SSH into your EC2 instance** (if not already connected):
   ```bash
   ssh -i "your-key-pair.pem" ec2-user@your-ec2-instance-ip
3. **Install the MySQL client on the EC2 instance**:
   ```bash
   sudo yum install mysql
4. **Connect to the RDS database from the EC2 instance**:
   ```bash
   mysql -h your-rds-endpoint -u your-username -p
5. **Create a database named `myappdb`**:
   ```sql
   CREATE DATABASE myappdb;
   USE myappdb;
6. **Run the database setup script to configure the tables and other database structures**:
   ```sql
   SOURCE setup-database.sql;
7. **Verify the database setup by checking the tables**:
   ```sql
   SHOW TABLES;
   EXIT;

### 3. Setting up the S3 Bucket
TODOOOO 
## Usage

- How to use the application once it's up and running.

## Application Design & Architecture

- Describe the design of your application.
- Explain how different components interact, especially if there are any virtual machines or cloud services involved.

## Cloud Deployment

- Detailed steps or scripts used for deploying the application to the cloud.
- Mention any manual steps required.

## Testing

- Describe how the application was tested.
- Mention any tools or frameworks used.

## Contributing

- Guidelines for anyone who wants to contribute to the project.

## License

- Mention the license of the project, if any.

## Acknowledgments

- Credit any third-party libraries, tools, or open-source projects used.
- Mention any inspirations or references.




