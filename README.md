# Task 2 — Containerization Using Docker and Deployment on a Cloud Virtual Machine

**Maincrafts Technology Internship | Cloud Computing & DevOps**

---

## Objective

Containerize the portfolio website from Task 1 using Docker and Nginx, then deploy it on an AWS EC2 cloud virtual machine.

---

## Project Structure

```
.
├── index.html        # Portfolio website (from Task 1)
├── styles.css        # Website styles
├── Dockerfile        # Docker build instructions
├── .dockerignore     # Files excluded from Docker build
└── README.md         # This file
```

---

## Step 1: Clone the Repository

```bash
git clone https://github.com/Rushikesh-Gade/-Maincrafts_Technology_Intership-task-2.git
cd -Maincrafts_Technology_Intership-task-2
```

---

## Step 2: Build the Docker Image

```bash
docker build -t portfolio-website .
```

Verify the image was created:

```bash
docker images
```

---

## Step 3: Run the Container Locally

```bash
docker run -d -p 8080:80 portfolio-website
```

Open browser and visit: `http://localhost:8080`

---

## Step 4: Deploy on AWS EC2

### 4.1 Launch EC2 Instance
- AMI: Ubuntu 22.04 LTS
- Instance type: t2.micro (Free Tier)
- Security group: Allow inbound traffic on port 80 (HTTP) and port 22 (SSH)
- Create or select a key pair (.pem file)

### 4.2 Connect to the VM

```bash
ssh -i your-key.pem ubuntu@<PUBLIC_IP>
```

### 4.3 Install Docker on the VM

```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker ubuntu
```

Log out and log back in for group changes to take effect.

### 4.4 Clone the Repo on the VM

```bash
git clone https://github.com/Rushikesh-Gade/-Maincrafts_Technology_Intership-task-2.git
cd -Maincrafts_Technology_Intership-task-2
```

### 4.5 Build and Run the Container on the VM

```bash
docker build -t portfolio-website .
docker run -d -p 80:80 portfolio-website
```

### 4.6 Access the Website

Open browser and visit: `http://<PUBLIC_IP>`

---

## Verify Running Container

```bash
docker ps
```

---

## Technologies Used

| Tool       | Purpose                          |
|------------|----------------------------------|
| Docker     | Containerization                 |
| Nginx      | Web server inside container      |
| AWS EC2    | Cloud virtual machine            |
| Git/GitHub | Version control & file transfer  |
| Ubuntu     | OS on the cloud VM               |

---

## Key Learnings

- How to write a Dockerfile using `nginx:alpine`
- Building and running Docker images locally
- Deploying a containerized app on a cloud VM
- Port mapping (`-p 80:80`) to expose container services
- Manual deployment workflow used before CI/CD automation
