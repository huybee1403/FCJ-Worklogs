---
title: "Install & Run Backend"
date: 2026-07-01
weight: 3
chapter: false
pre: " <b> 5.3.3. </b> "
---

<div class="lms">

# Install and run the backend on EC2

Connect to the EC2 instance via SSH, set up the environment, and run the backend application.

**Open Terminal/PowerShell in the folder containing the key.**
![Open the terminal](/images/Screenshot%202026-07-09%20230133.png)

**SSH into the EC2 instance using `ssh -i "Khanh.pem" ec2-user@<public-dns>`.**
![Connect to EC2 via SSH](/images/Screenshot%202026-07-09%20230210.png)

**Update the system and install `git` (`sudo dnf update -y`, `sudo dnf install git -y`).**
![Update the system and install git](/images/Screenshot%202026-07-09%20230221.png)

**The git installation completes.**
![Git installation completed](/images/Screenshot%202026-07-09%20230254.png)

**Install Node.js (`sudo dnf install nodejs -y`).**
![Install Node.js](/images/Screenshot%202026-07-09%20230304.png)

**Clone the LMS source code, enter the `backend` folder, and run `npm install`.**
![Clone the source code and install dependencies](/images/Screenshot%202026-07-09%20230320.png)

**Download the DocumentDB CA certificate (`global-bundle.pem`), do a test run with `npm start` (DB connection successful, port 8080), then install PM2.**
![Download CA cert, test run, and install PM2](/images/Screenshot%202026-07-09%20230354.png)

**Verify that PM2 is installed (`pm2 -v`).**
![Check the PM2 version](/images/Screenshot%202026-07-09%20230401.png)

**Run the backend in the background with `pm2 start server.js --name backend`, then `pm2 save` for automatic restart.**
![Run the backend with PM2 and save the configuration](/images/Screenshot%202026-07-09%20230533.png)

</div>
