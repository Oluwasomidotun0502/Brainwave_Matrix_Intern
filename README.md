## Brainwave Matrix Solution

brainwave_matrix_intern/
│
├── index.html              # Main web page
├── README.md               # This guide with detailed steps
├── snapshots/              # Folder for snapshots of EC2, Python server, GitHub, and S3
│   ├── ec2_ssh_terminal.png
│   ├── python3_server.png
│   ├── git_push_terminal.png
│   ├── aws_s3_bucket_setup.png
│   └── aws_static_hosting.png


## Project Overview

The Brainwave Matrix Solution is a simple web application deployed on AWS to demonstrate internship tasks.

## It showcases:

Launching and connecting to an AWS EC2 instance using a PEM key

Local testing of the web page with Python HTTP server

GitHub version control with commits and pushes

Deployment of a static website on AWS S3

Snapshots to verify each step

This project serves as a record of the deployment process and demonstrates cloud hosting capabilities.

1. AWS EC2 Instance Setup

Step 1: Launch EC2 Instance

Navigate to EC2 → Launch Instance

Instance Name: Brainwave-Matrix-EC2

AMI: Ubuntu Server 22.04 LTS (64-bit x86/ARM)

Instance Type: t2.micro (Free Tier eligible)

Key Pair: Create or select an existing .pem key

Security Group: Allow inbound SSH (port 22) from your IP

Step 2: Connect to the Instance

chmod 400 brainwave-key.pem
ssh -i brainwave-key.pem ubuntu@ec2-184-72-161-140.compute-1.amazonaws.com


Step 3: Verify Connection

pwd
ls -l


Snapshot: snapshots/ec2_ssh_terminal.png

2. Local Setup and Testing

Step 1: Navigate to project folder

cd ~/brainwave_matrix_intern


Step 2: Run a local Python HTTP server

python3 -m http.server 8080


Open your browser and visit:

http://localhost:8080


Snapshot: snapshots/python3_server.png

3. GitHub Repository Setup

Step 1: Initialize Git repository

git init
git branch -M main


Step 2: Configure Git identity

git config --global user.name "Oluwasomidotun Adepitan"
git config --global user.email "anuoluwapodotun@gmail.com"


Step 3: Add project files and commit

git add .
git commit -m "Add Brainwave Matrix solution HTML"


Step 4: Add remote and push to GitHub

git remote add origin https://github.com/Oluwasomidotun0502/Brainwave_Matrix_Intern.git
git push -u origin main --force


Snapshot: snapshots/git_push_terminal.png

4. AWS S3 Deployment

Step 1: Create an S3 bucket

aws s3 mb s3://brainwave-matrix-intern


Step 2: Sync project files to S3

aws s3 sync ~/brainwave_matrix_intern s3://brainwave-matrix-intern


Step 3: Enable static website hosting

aws s3 website s3://brainwave-matrix-intern --index-document index.html


Snapshots:

snapshots/aws_s3_bucket_setup.png

snapshots/aws_static_hosting.png

Step 4: Access live site
https://brainwave-matrix-intern.s3.amazonaws.com/index.html


Screenshots are included for verification of each step.

Commands shown in this README provide proof of work and reproducibility.
