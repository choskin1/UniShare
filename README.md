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

### 1. Setting up the RDS for Database

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
### 2. Setting Up an Amazon S3 Bucket

1. **Sign in to AWS**:
   - Go to [AWS Console](https://aws.amazon.com/) and sign in.
2. **Access S3**:
   - Select "S3" from Services or search for it.
3. **Create Bucket**:
   - Click "Create bucket".
   - Name it (names are globally unique) and choose a region.
4. **Configure Settings**:
   - Adjust "Properties" and "Permissions" as needed.
   - UniShare currently alows anyone to upload files with an open policy

### 3. Setting up the EC2 for Web Server

1. **Launch an EC2 instance** on AWS and ensure it's running.
2. **SSH into the EC2 instance** using your preferred terminal or SSH client:
   ```bash
   ssh -i "your-key-pair.pem" ec2-user@your-ec2-instance-ip
3. **Clone the UniShare repository**:
   ```bash
   sudo yum install git
   git clone https://github.com/choskin1/UniShare.git
4. **Setup the connection to the database** by changing line 13 in main, the result should look like this
    ```bash
    app.config['SQLALCHEMY_DATABASE_URI'] = 'mysql+pymysql://<username>:<passoword>@<database endpoint>/myappdb'
5. **Setup the connection to the s3 bucket** by ensuring that the name of the bucket is approipately referenced in upload_to_s3() and in view_files()
5. **Navigate to the cloned repository** and run the frontend startup script:
   ```bash
   cd UniShare
   ./setup-frontend.sh
6. This will start the main Python application and create a server operating on port `5001`.

## Usage

### 🌐 Accessing UniShare:

1. **Open a Web Browser**: Navigate to the public IP address of the Web Server EC2, dont forget to specify port 5001
2. **Sign In**: If you're a new user, follow the registration process otherwise sign in using your existing credentials

### 📖 Study Groups:

1. **Browse Existing Groups**: Check out study groups that match your interests or subjects.
2. **Join a Group**: Click on a group and hit the 'Join' button. Some groups may require approval from the group admin.
3. **Create a Group**: Can't find a group that matches your needs? Create one! Click on 'Create Group', fill in the details, and invite members.

### 📁 Sharing Files:

1. **Access the File Section**: Within a study group, navigate to the 'Files' tab.
2. **Upload a File**: Click on 'Upload', select your file. The file will be stored securely in the S3 bucket.
3. **Download Files**: Browse through shared files and click 'Download' next to the file you wish to access.

### 📹 Video Conferencing:

1. **Schedule a Session**: Within a study group, navigate to the 'Video Sessions' tab and schedule a new session.
2. **Join a Session**: Click on the scheduled session link at the specified time to join the video conference.

### 🔒 Privacy & Security:

- All your interactions, including file uploads and video sessions, are encrypted and secure.
- Ensure you log out after each session, especially when accessing from public devices.

Remember, UniShare is all about collaboration. Engage, share, and make the most of this platform!


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




