# Deployment Notes — Task 2

## Docker Container Running on AWS EC2

### EC2 Instance Details
- **Public IP:** 35.154.189.28
- **OS:** Ubuntu 22.04 LTS
- **Instance Type:** t2.micro (Free Tier)
- **Region:** ap-south-1 (Mumbai)

### Live Website URL
> http://35.154.189.28

### Docker Container Status (docker ps output)
```
CONTAINER ID   IMAGE               STATUS         PORTS                          NAMES
21ecd2ea81ba   portfolio-website   Up 2 minutes   0.0.0.0:80->80/tcp, [::]:80->80/tcp   awesome_brahmagupta
```

### Docker Image Details
```
Image:   portfolio-website:latest
Base:    nginx:alpine
Port:    80
```

### Commands Used on EC2
```bash
# Install Docker
sudo apt update -y
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker

# Clone repo
git clone https://github.com/Rushikesh-Gade/-Maincrafts_Technology_Intership-task-2.git

# Build image
sudo docker build -t portfolio-website .

# Run container
sudo docker run -d -p 80:80 portfolio-website

# Verify
sudo docker ps
```

### Access
Open browser: http://35.154.189.28
