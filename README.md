# 🚀 DevOps Mini Project — Automated CI/CD Pipeline

A production-ready CI/CD pipeline that automatically tests, builds, and deploys a Flask web app to AWS ECS Fargate using GitHub Actions and Docker.

---

## 🏗️ Architecture

```
Developer → GitHub Push
                │
                ▼
        GitHub Actions
        ┌───────────────────────────────┐
        │  1. Run Tests (pytest)        │
        │  2. Build Docker Image        │
        │  3. Push to AWS ECR           │
        │  4. Deploy to AWS ECS Fargate │
        └───────────────────────────────┘
                │
                ▼
        Live App on AWS ECS
        (Public URL)
```

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Python + Flask | Web application |
| pytest | Automated testing |
| Docker | Containerization |
| GitHub Actions | CI/CD pipeline |
| AWS ECR | Container image registry |
| AWS ECS Fargate | Serverless container hosting |
| AWS IAM | Credentials & permissions |

---

## 📁 Project Structure

```
devops-mini-project/
├── app.py                          # Flask application
├── requirements.txt                # Python dependencies
├── Dockerfile                      # Container definition
├── conftest.py                     # Pytest configuration
├── tests/
│   └── test_app.py                 # Unit tests
└── .github/
    └── workflows/
        └── deploy.yml              # CI/CD pipeline
```

---

## 🚦 API Endpoints

| Endpoint | Method | Response |
|---|---|---|
| `/` | GET | `{"message": "Hello from my DevOps app!", "status": "running"}` |
| `/health` | GET | `{"status": "healthy"}` |
| `/version` | GET | `{"version": "1.0.0"}` |

---

## ⚙️ CI/CD Pipeline Flow

Every `git push` to `main` triggers the following automatically:

1. **Test** — runs `pytest` to validate all endpoints
2. **Build** — builds a Docker image tagged with the commit SHA
3. **Push** — pushes the image to AWS Elastic Container Registry (ECR)
4. **Deploy** — updates the ECS Fargate service with the new image

---

## 🏃 Run Locally

### Prerequisites
- Python 3.11+
- Docker Desktop
- Git

### Steps

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/devops-mini-project.git
cd devops-mini-project

# Create and activate virtual environment
python3 -m venv venv
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Run tests
pytest tests/ -v

# Run the app
python app.py
```

Visit `http://localhost:5000` in your browser.

### Run with Docker

```bash
# Build the image
docker build -t my-devops-app .

# Run the container
docker run -p 5000:5000 my-devops-app
```

---

## ☁️ AWS Setup

### Prerequisites
- AWS account
- AWS CLI installed and configured

### Resources Created

| Resource | Name |
|---|---|
| ECR Repository | `app/my-devops-app` |
| ECS Cluster | `my-cluster001` |
| ECS Service | `my-app-service` |
| ECS Task Definition | `my-app-task` |

### Required IAM Permissions

Attach these policies to your AWS IAM user:
- `AmazonEC2ContainerRegistryFullAccess`
- `AmazonECS_FullAccess`
- `AmazonVPCFullAccess`

---

## 🔐 GitHub Secrets Required

Go to your GitHub repo → **Settings → Secrets and variables → Actions** and add:

| Secret | Description |
|---|---|
| `AWS_ACCESS_KEY_ID` | Your AWS IAM access key |
| `AWS_SECRET_ACCESS_KEY` | Your AWS IAM secret key |

---

## 📊 What This Project Demonstrates

- ✅ **CI/CD automation** — zero manual deployment steps
- ✅ **Containerization** — app runs identically everywhere via Docker
- ✅ **Cloud deployment** — serverless hosting on AWS Fargate
- ✅ **Security best practices** — credentials stored as GitHub secrets, never in code
- ✅ **Test-driven pipeline** — deployment blocked if tests fail
- ✅ **Infrastructure as code mindset** — all config stored in version control

---

## 👤 Author

**Phoungpagaloungprom**
- GitHub: [@YOUR_USERNAME](https://github.com/Memodz)

---

## 📄 License

MIT License — feel free to use this project as a template for your own DevOps work.


# miniProject

source venv/bin/activate
echo 'venv/' >> .gitignore #work
