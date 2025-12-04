# 🚀 Shopping Cart CI/CD Pipeline with Jenkins

## 📘 Project Overview
This project demonstrates a complete **End-to-End CI/CD pipeline** for a *Shopping Cart Application* using **Jenkins**, **Maven**, **SonarQube**, **OWASP Dependency Check**, and **Docker**.  
The pipeline automates code compilation, static code analysis, security checks, Docker image creation, and deployment, with access to the application to test admin and regular user flows.

---

## 🧩 Tech Stack
- **Jenkins** – CI/CD automation server  
- **Maven** – Build and dependency management  
- **SonarQube** – Code quality and static analysis  
- **OWASP Dependency Check** – Security vulnerability scanning  
- **Docker** – Containerization and deployment  
- **GitHub** – Source code repository  
- **Credentials & Environment Variables** – GitHub, Docker Hub, SonarQube tokens

---

## 🏗 Project Architecture

![Pipeline Architecture](screenshots/01-plugins.png)

---

## ⚙ Repo Layout

project-root/
│
├── Jenkinsfile                  # CI/CD pipeline definition
├── docker/
│   └── Dockerfile               # Dockerfile for the application
├── src/                         # Application source code
│   ├── main/
│   └── test/
├── reports/
│   ├── dependency-check-report.html
│   └── dependency-check-report.xml
├── screenshots/
│   ├── 01-plugins.png
│   ├── 02-add-jdk-tool.png
│   ├── 03-add-sonarqube-tool.png
│   ├── 04-add-maven-tool.png
│   ├── 05-add-dependency-check-tool.png
│   ├── 06-add-docker-tool.png
│   ├── 07-checkout-compile-stages.png
│   ├── 08-console-output-for-first-tow-stages.png
│   ├── 09-add-owasp-stage.png
│   ├── 10-build-owasp-stage.png
│   ├── 11-genrate-xml-html-reports.png
│   ├── 12-run-sonar-as-container.png
│   ├── 13-credentials.png
│   ├── 14-configure-sonar-server.png
│   ├── 15-add-sonarqube-stage.png
│   ├── 16-build-sonarqube-stage.png
│   ├── 17-sonar-analysis.png
│   ├── 18-Dockerfile.png
│   ├── 19-add-maven-build-and-docker-build&push-stages.png
│   ├── 20-image-pushed.png
│   ├── 21-add-deploy-stage.png
│   ├── 22-build-deploy-stage.png
│   ├── 23-shopping-cart-container.png
│   ├── 24-access-app.png
│   ├── 25-buy-product-root-admin.png
│   ├── 26-create-new-user.png
│   └── 27-buy-product-regular-user.png
└── README.md

- All screenshots are stored in **screenshots/**  
- Reports are stored in **reports/**  

---

## 📸 Key Screenshots

| #  | Screenshot                          | Description                                                                 |
|----|-------------------------------------|-----------------------------------------------------------------------------|
| 01 | ![plugins](screenshots/01-plugins.png) | Jenkins plugins installed (SonarQube, Maven, OWASP Dependency Check, Docker) |
| 02 | ![jdk-tool](screenshots/02-add-jdk-tool.png) | Added JDK tool in Jenkins                                                    |
| 03 | ![sonarqube-tool](screenshots/03-add-sonarqube-tool.png) | Added SonarQube scanner tool                                                |
| 04 | ![maven-tool](screenshots/04-add-maven-tool.png) | Added Maven tool                                                            |
| 05 | ![dependency-check-tool](screenshots/05-add-dependency-check-tool.png) | Added OWASP Dependency Check tool                                           |
| 06 | ![docker-tool](screenshots/06-add-docker-tool.png) | Added Docker tools                                                          |
| 07 | ![checkout-compile](screenshots/07-checkout-compile-stages.png) | Git checkout and Maven compile stages                                       |
| 08 | ![console-output](screenshots/08-console-output-for-first-tow-stages.png) | Console output for checkout and compile                                     |
| 09 | ![owasp-stage](screenshots/09-add-owasp-stage.png) | OWASP Dependency Check stage added                                          |
| 10 | ![build-owasp](screenshots/10-build-owasp-stage.png) | OWASP Dependency Check build executed                                       |
| 11 | ![reports](screenshots/11-genrate-xml-html-reports.png) | Generated XML & HTML reports                                               |
| 12 | ![sonar-container](screenshots/12-run-sonar-as-container.png) | Running SonarQube in a container                                           |
| 13 | ![credentials](screenshots/13-credentials.png) | GitHub, Docker Hub, SonarQube credentials set in Jenkins                    |
| 14 | ![configure-sonar](screenshots/14-configure-sonar-server.png) | Configure SonarQube server in Jenkins                                      |
| 15 | ![sonar-stage](screenshots/15-add-sonarqube-stage.png) | Added SonarQube stage in pipeline                                           |
| 16 | ![build-sonar](screenshots/16-build-sonarqube-stage.png) | SonarQube stage build output                                               |
| 17 | ![sonar-analysis](screenshots/17-sonar-analysis.png) | SonarQube web UI showing project analysis                                   |
| 18 | ![dockerfile](screenshots/18-Dockerfile.png) | Dockerfile used to build application image                                  |
| 19 | ![docker-build](screenshots/19-add-maven-build-and-docker-build&push-stages.png) | Docker build & push stage added                                             |
| 20 | ![image-pushed](screenshots/20-image-pushed.png) | Docker image successfully pushed to Docker Hub                               |
| 21 | ![deploy-stage](screenshots/21-add-deploy-stage.png) | Deploy stage added in pipeline                                              |
| 22 | ![deploy-build](screenshots/22-build-deploy-stage.png) | Console output of deploy stage                                              |
| 23 | ![container-running](screenshots/23-shopping-cart-container.png) | Application container running in Docker                                      |
| 24 | ![access-app](screenshots/24-access-app.png) | Access application homepage                                                 |
| 25 | ![admin-buy](screenshots/25-buy-product-root-admin.png) | Admin user buys products, Shopping Cart updated                             |
| 26 | ![create-user](screenshots/26-create-new-user.png) | Create new user account                                                     |
| 27 | ![user-buy](screenshots/27-buy-product-regular-user.png) | Regular user buys product, Shopping Cart updated                             |

---

## 🧠 Workflow Explanation

1. Plugins & Tools Setup – Install Jenkins plugins and configure tools (JDK, Maven, SonarQube, Docker, OWASP Dependency Check).  
2. Git Checkout & Compile – Pull code from GitHub and compile using Maven.  
3. OWASP Dependency Check – Run dependency vulnerability analysis; generate HTML and XML reports.  
4. SonarQube Scan – Analyze code quality using SonarQube in a Docker container.  
5. Docker Build & Push – Build Docker image from Dockerfile and push to Docker Hub.  
6. Deploy Stage – Deploy the container with proper environment variables and verify running container.  
7. Application Demo – Admin buys products; create a new user and perform purchase as regular user. Verify Shopping Cart updates.

---

## 📦 Deployment Commands

mvn clean package -Dskiptest=true  
docker build -t shopping-cart -f docker/Dockerfile .  
docker tag shopping-cart a7medsayed/shopping-cart:latest  
docker push a7medsayed/shopping-cart:latest  
docker run -d --name merch-shop -p 8070:8070 -e JAVA_OPTS="-Xms128m -Xmx512m -Djava.security.egd=file:/dev/./urandom -Djava.io.tmpdir=/tmp" a7medsayed/shopping-cart:latest

---

## 🔒 Credentials & Environment Variables

- GitHub – Jenkins GitHub credentials  
- Docker Hub – Jenkins Docker Hub credentials  
- SonarQube – SonarQube token/credentials  
- Environment Variables – SCANNER_HOME (SonarQube Scanner), JAVA_OPTS for deployment

---

## 🧠 Summary

End-to-end CI/CD pipeline for Shopping Cart application  
Automated build, compile, security scan, and static analysis  
Dockerized deployment with container verification  
Admin & regular user flows tested and verified  
Jenkins integration with SonarQube, OWASP Dependency Check, and Docker Hub

---

## 👤 Author

Ahmed Sayed  
LinkedIn: https://www.linkedin.com/in/ahmed-sayed-devops-cloud  
GitHub: https://github.com/ahmed-sayed-devops

---

## 📜 License

MIT License – see LICENSE file for details
