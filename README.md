# 🧮 Assignment 8 - FastAPI Calculator Web Application

**Author:** Jailene Agosto  
**GitHub:** [jaiagosto](https://github.com/jaiagosto)  
**Docker Hub:** [jaiagosto](https://hub.docker.com/u/jaiagosto)

---

## 📋 Project Overview

This is a web-based calculator application built with FastAPI. It performs basic arithmetic operations like addition, subtraction, multiplication, and division. The project includes comprehensive testing (unit tests, integration tests, and end-to-end tests) and uses Docker for containerization with a complete CI/CD pipeline through GitHub Actions.

**Live Application:** The calculator runs at `http://localhost:8000` and has a simple web interface where you can input two numbers and perform calculations.

---

## 🎯 Features

- ✅ **Addition** - Add two numbers together
- ✅ **Subtraction** - Subtract one number from another
- ✅ **Multiplication** - Multiply two numbers
- ✅ **Division** - Divide numbers (with proper error handling for division by zero)
- ✅ **Web Interface** - Easy-to-use HTML interface
- ✅ **REST API** - JSON-based API endpoints for all operations
- ✅ **Comprehensive Testing** - Unit, integration, and E2E tests
- ✅ **Logging** - Track operations and errors
- ✅ **CI/CD Pipeline** - Automated testing and deployment

---

## 🛠️ Technologies Used

- **FastAPI** - Modern web framework for building APIs
- **Python 3.10** - Programming language
- **Pytest** - Testing framework
- **Playwright** - Browser automation for E2E tests
- **Docker** - Containerization platform
- **GitHub Actions** - CI/CD automation
- **Uvicorn** - ASGI web server

---

## 📁 Project Structure
```
assignment8/
├── app/
│   ├── __init__.py
│   └── operations.py          # Math operations (add, subtract, multiply, divide)
├── templates/
│   └── index.html             # Web interface
├── tests/
│   ├── __init__.py
│   ├── unit/
│   │   ├── __init__.py
│   │   └── test_calculator.py # Unit tests for operations
│   ├── integration/
│   │   ├── __init__.py
│   │   └── test_fastapi_calculator.py # API endpoint tests
│   └── e2e/
│       ├── __init__.py
│       ├── conftest.py        # E2E test setup
│       └── test_e2e.py        # Browser-based tests
├── .github/
│   └── workflows/
│       └── ci-cd.yml          # GitHub Actions workflow
├── .vscode/
│   └── settings.json          # VS Code pytest settings
├── main.py                    # Main FastAPI application
├── requirements.txt           # Python dependencies
├── Dockerfile                 # Docker image instructions
├── docker-compose.yml         # Docker Compose configuration
├── pytest.ini                 # Pytest configuration
├── .gitignore                 # Git ignore rules
├── LICENSE                    # MIT License
└── README.md                  # This file
```

---

## 🚀 Getting Started

### Prerequisites

Before you start, make sure you have:
- Python 3.10 or higher
- Git
- Docker (optional, for containerization)

---

### 📦 1. Clone the Repository
```bash
git clone https://github.com/jaiagosto/assignment8.git
cd assignment8
```

---

### 🐍 2. Set Up Python Virtual Environment

**Create the virtual environment:**
```bash
python3 -m venv venv
```

**Activate the virtual environment:**

- **Mac/Linux:**
```bash
source venv/bin/activate
```

- **Windows:**
```bash
venv\Scripts\activate
```

You should see `(venv)` at the beginning of your terminal prompt.

---

### 📥 3. Install Dependencies
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

**Install Playwright browsers (for E2E tests):**
```bash
playwright install
```

**On Linux, you may also need:**
```bash
sudo playwright install-deps
```

---

### ▶️ 4. Run the Application

**Start the FastAPI server:**
```bash
python main.py
```

**Or with uvicorn directly:**
```bash
uvicorn main:app --reload
```

**Open your browser and go to:**
```
http://localhost:8000
```

You should see "Hello World" and the calculator interface!

---

## 🧪 Running Tests

### Run All Tests
```bash
pytest
```

### Run Unit Tests Only
```bash
pytest tests/unit/ -v
```

**Expected output:** 21 tests should pass ✅

### Run Integration Tests Only
```bash
pytest tests/integration/ -v
```

**Expected output:** 5 tests should pass ✅

### Run End-to-End Tests Only
```bash
pytest tests/e2e/ -v -m e2e
```

**Expected output:** 3 tests should pass ✅

### Run Tests with Coverage Report
```bash
pytest tests/unit/ tests/integration/ --cov=app --cov-report=html
```

This creates an HTML coverage report in the `htmlcov/` folder.  
Open `htmlcov/index.html` in your browser to view it.

**Expected coverage:** 100% ✅

---

## 🐳 Docker Setup

### Build the Docker Image
```bash
docker build -t jaiagosto/assignment8 .
```

### Run the Docker Container
```bash
docker run -p 8000:8000 jaiagosto/assignment8
```

### Or Use Docker Compose
```bash
docker-compose up
```

**Access the application at:**
```
http://localhost:8000
```

**Stop the container:**
```bash
docker-compose down
```

---

## 🌐 API Endpoints

### GET /
Returns the HTML calculator interface

### POST /add
**Request:**
```json
{
  "a": 10,
  "b": 5
}
```
**Response:**
```json
{
  "result": 15
}
```

### POST /subtract
**Request:**
```json
{
  "a": 10,
  "b": 5
}
```
**Response:**
```json
{
  "result": 5
}
```

### POST /multiply
**Request:**
```json
{
  "a": 10,
  "b": 5
}
```
**Response:**
```json
{
  "result": 50
}
```

### POST /divide
**Request:**
```json
{
  "a": 10,
  "b": 2
}
```
**Response:**
```json
{
  "result": 5.0
}
```

**Division by zero error:**
```json
Request: {"a": 10, "b": 0}
Response: {"error": "Cannot divide by zero!"}
Status Code: 400
```

### GET /health
Health check endpoint for Docker
```json
{
  "status": "healthy"
}
```

---

## 🔄 CI/CD Pipeline

The project uses **GitHub Actions** for automated testing and deployment.

**Pipeline stages:**

1. **Test Stage** - Runs all unit, integration, and E2E tests
2. **Security Stage** - Scans Docker image for vulnerabilities using Trivy
3. **Deploy Stage** - Builds and pushes Docker image to Docker Hub

**View the workflow:**
- Go to your GitHub repository
- Click the "Actions" tab
- See the workflow runs and results

**Secrets needed in GitHub:**
- `DOCKERHUB_USERNAME` - Your Docker Hub username (jaiagosto)
- `DOCKERHUB_TOKEN` - Your Docker Hub access token

---

## 📊 Test Coverage

- **Unit Tests:** 100% coverage of `operations.py`
- **Integration Tests:** All 5 API endpoints tested
- **E2E Tests:** Full browser-based user workflow testing

**Total:** 29 tests (21 unit + 5 integration + 3 E2E)

---

## 🔥 Useful Commands Cheat Sheet

| Action                          | Command                                          |
| ------------------------------- | ------------------------------------------------ |
| Activate virtual environment    | `source venv/bin/activate`                       |
| Install dependencies            | `pip install -r requirements.txt`                |
| Run application                 | `python main.py`                                 |
| Run all tests                   | `pytest`                                         |
| Run tests with coverage         | `pytest --cov=app`                               |
| Build Docker image              | `docker build -t jaiagosto/assignment8 .`        |
| Run Docker container            | `docker run -p 8000:8000 jaiagosto/assignment8` |
| Start with Docker Compose       | `docker-compose up`                              |
| Stop Docker Compose             | `docker-compose down`                            |
| Push to GitHub                  | `git add . && git commit -m "message" && git push` |

---

## 📝 Assignment Requirements Checklist

- ✅ FastAPI calculator application with all arithmetic operations
- ✅ Unit tests for `operations.py` functions
- ✅ Integration tests for all API endpoints
- ✅ End-to-end tests using Playwright
- ✅ Logging implemented throughout the application
- ✅ GitHub Actions CI/CD workflow configured
- ✅ Docker containerization with Dockerfile
- ✅ All tests passing locally and in CI/CD
- ✅ README documentation
- ✅ Regular Git commits with descriptive messages

---

## 📎 Links

- **GitHub Repository:** https://github.com/jaiagosto/assignment8
- **Docker Hub:** https://hub.docker.com/r/jaiagosto/assignment8

---

## 📄 License

MIT License - See LICENSE file for details

---

## 👩‍💻 Author

**Jailene Agosto**  
Assignment: Module 8 - FastAPI Calculator
 
