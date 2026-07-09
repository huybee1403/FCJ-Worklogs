---
title: "Deploy Frontend with Amplify"
date: 2026-07-01
weight: 2
chapter: false
pre: " <b> 5.4.2. </b> "
---

<div class="lms">

# Deploy the web frontend with AWS Amplify

Deploy the frontend (React/Vite) from GitHub to AWS Amplify.

**Open the AWS Amplify service.**
![Navigate to AWS Amplify](/images/Screenshot%202026-07-09%20230957.png)

**Select GitHub as the source and grant access.**
![Select the GitHub source](/images/Screenshot%202026-07-09%20231022.png)

**Select the `LMS_System_MongoDB` repo, the `main` branch, and mark it as a monorepo with the root directory `frontend`.**
![Select the repo, branch, and monorepo directory](/images/Screenshot%202026-07-09%20231056.png)

**Configure the build: command `npm run build`, output directory `dist`.**
![Configure the application build](/images/Screenshot%202026-07-09%20231113.png)

**Add the environment variable `VITE_BACKEND_URL = https://api.fixing404.win/api` so the frontend can call the backend.**
![Add the VITE_BACKEND_URL environment variable](/images/Screenshot%202026-07-09%20231228.png)

**Review the repo and branch configuration.**
![Review the configuration (1)](/images/Screenshot%202026-07-09%20231239.png)

**Review the advanced settings and environment variables, then Save and deploy.**
![Review the configuration (2)](/images/Screenshot%202026-07-09%20231245.png)

**Deployment successful — the application runs at the `*.amplifyapp.com` domain.**
![Application successfully deployed on Amplify](/images/Screenshot%202026-07-09%20231300.png)

</div>
