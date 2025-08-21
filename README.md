# Medical_chatbot

### Create a conda environment
``` bash
conda create -n myenv python=3.10 -y
```
```bash
conda activate myenv 
```

### Install the requirements
```bash
pip install -r requirements.txt
```

# AWS-CICD-Deployment-with-Github-Actions

## 1. Login to AWS console.

## 2. Create IAM user for deployment

### With specific access:
- **EC2 access:** It is a virtual machine.
- **ECR:** Elastic Container Registry to save your Docker image in AWS.

---

## Description: About the deployment

1. Build Docker image of the source code.
2. Push your Docker image to ECR.
3. Launch your EC2 instance.
4. Pull your image from ECR on EC2.
5. Launch your Docker image in EC2.

---

## Policy:

1. Attach **AmazonEC2ContainerRegistryFullAccess**.
2. Attach **AmazonEC2FullAccess**.
3. Create ECR repository to store/save Docker images.

   - Save the URI (example):  
     `411711548352.dkr.ecr.us-east-1.amazonaws.com/medicalchatbot`

4. Create EC2 machine (Ubuntu).
5. Open EC2 and install Docker in EC2 machine:

### Optional:
sudo apt-get update -y
sudo apt-get upgrade

    
### Required:
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker ubuntu
newgrp docker


6. Configure EC2 as self-hosted GitHub Actions runner:

- Go to **Settings > Actions > Runners > New self-hosted runner**.
- Choose OS.
- Run the displayed commands one by one on your EC2 instance.

7. Setup GitHub repository Secrets (Settings > Secrets and variables > Actions):

- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
- `AWS_DEFAULT_REGION`
- `ECR_REPO`
- `PINECONE_API_KEY`
- `OPENAI_API_KEY`
