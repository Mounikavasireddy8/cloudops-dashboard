# CloudOps Dashboard — Docker + AWS EC2

Personal DevOps portfolio containerized with Docker and 
deployed live on AWS EC2.

## Live Deployment
Application was live at http://13.127.97.204 on AWS EC2
![CloudOps Dashboard Live on AWS](screenshot.png)
(stopped to avoid free tier charges — can redeploy in 10 minutes)

## Tech Stack
- Docker + Dockerfile
- nginx:1.25-alpine (23MB optimized image)
- AWS EC2 — Amazon Linux 2023
- SSH + SCP deployment
- Non-root user security (appuser)
- Docker Compose for local development

## How to run locally
git clone https://github.com/YOUR_USERNAME/cloudops-dashboard
cd cloudops-dashboard
docker compose up -d
Open http://localhost:8080

## Deployment pipeline
1. Write code + Dockerfile on laptop
2. Test locally with Docker Compose
3. Launch AWS EC2 — Amazon Linux 2023
4. SSH into EC2 using .pem key
5. SCP project files to EC2
6. Install Docker on EC2
7. docker build -t cloudops-dashboard:v1 .
8. docker run -d -p 80:80 cloudops-dashboard:v1
9. Access via EC2 public IP from anywhere

## Security practices applied
- Non-root user — runs as appuser not root
- Pinned base image — nginx:1.25-alpine
- Minimal attack surface — Alpine Linux 23MB
- .dockerignore — prevents secret files in image
- Resource limits — 256MB RAM, 0.5 CPU

## Project structure
cloudops-dashboard/
├── Dockerfile
├── docker-compose.yml
├── nginx.conf
├── .dockerignore
└── app/
    └── index.html

## Skills demonstrated
Docker, Dockerfile, Docker Compose, AWS EC2, SSH, SCP,
nginx, Alpine Linux, Linux CLI, AWS CLI, DevOps pipeline
