# -DevOps-Journey-Week-14-Docker-Docker-Compose-Kubernetes
This repo documents my hands-on journey with containerization and orchestration.  
Covered topics: Docker networking, multi-container apps with Docker Compose, and Kubernetes for scaling.

---

## 🔹 Docker Networking

### 1. Bridge (default)
```bash
docker run -dit --name app1 busybox
docker run -dit --name app2 busybox
docker network ls
2. Host
bash
Copy code
docker run -dit --network host nginx
3. Overlay (Swarm)
bash
Copy code
docker swarm init
docker network create -d overlay myoverlay
docker service create --name web --network myoverlay nginx
## 🔹 Docker Compose for Multi-Container Apps
docker-compose.yml example:

yaml
Copy code
version: "3.9"
services:
  web:
    image: nginx
    ports:
      - "8080:80"
  db:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: myapp
Commands:

bash
Copy code
docker-compose up -d
docker-compose logs -f
docker-compose down
## 🔹 Kubernetes for Scaling & Automation
bash
Copy code
# Create deployment
kubectl create deployment web --image=nginx

# Expose service
kubectl expose deployment web --type=NodePort --port=80

# Scale
kubectl scale deployment web --replicas=5
Features:
Auto-scaling

Self-healing

Rolling updates

Load balancing

📌 This repo acts as a reference guide with commands and concepts.
Use it to quickly recall commands and understand where Docker ends and Kubernetes begins.
My Portfolio: [azmatahmed.netlify.app](https://azmatahmed.netlify.app/)
#docker #kubernetes #devops
