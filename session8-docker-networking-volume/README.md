# Docker Networking and Volumes — Homework

## Task 1: Docker Container Networking

### Create Three Docker Networks

```bash
docker network create frontend-net
docker network create backend-net
docker network create database-net

docker network ls
```

### Create the Frontend, Backend, and Database Containers

```bash
docker run -d \
  --name frontend \
  --network frontend-net \
  nginx:alpine

docker run -d \
  --name backend \
  --network frontend-net \
  alpine:3.20 \
  sleep infinity

docker network connect backend-net backend

docker run -d \
  --name database \
  --network backend-net \
  -e MYSQL_ROOT_PASSWORD=DevOpsTest123! \
  -e MYSQL_DATABASE=appdb \
  mysql:8.4

docker network connect database-net database
```

### Verify Network Connections

```bash
docker network inspect frontend-net
docker network inspect backend-net
docker network inspect database-net

docker inspect frontend
docker inspect backend
docker inspect database
```

### Test Connectivity

Check that the backend can reach the frontend:

```bash
docker exec backend ping -c 3 frontend
```

Check that the backend can reach the database:

```bash
docker exec backend ping -c 3 database
```

Check the MySQL port from the backend:

```bash
docker exec backend sh -c \
  "nc -zvw 3 database 3306"
```

**Expected result:** The backend should resolve the container names and reach the frontend and database over their shared networks. MySQL may take some time to initialize.

## Task 2: Host Network

Pull the Apache HTTP Server image:

```bash
docker pull httpd:2.4
```

On a native Linux host, run Apache using host networking:

```bash
docker run -d \
  --name apache-host \
  --network host \
  httpd:2.4
```

Verify the service:

```bash
docker ps
curl http://localhost:80
```

**Expected result:** The default Apache page's HTML is returned.

**macOS note:** Docker Desktop does not provide the same host networking behavior as native Linux in every configuration. If host networking is unavailable, use the following port-mapped alternative to access Apache:

```bash
docker run -d \
  --name apache-host \
  -p 8086:80 \
  httpd:2.4

curl http://localhost:8086
```

## Task 3: Bind Mount

Create a local directory and HTML file:

```bash
mkdir -p bind-mount-site
cd bind-mount-site

echo "Hello students" > index.html

cd ..
```

Run Nginx with the directory mounted into its web root:

```bash
docker run -d \
  --name bind-mount-nginx \
  -p 8085:80 \
  --mount type=bind,src="$(pwd)/bind-mount-site",dst=/usr/share/nginx/html,readonly \
  nginx:alpine
```

Verify the website:

```bash
curl http://localhost:8085
```

Expected output:

```text
Hello students
```

Modify the local HTML file:

```bash
echo "<h1>Updated Hello students</h1>" > bind-mount-site/index.html
```

Verify the update without restarting the container:

```bash
curl http://localhost:8085
docker ps
```

Expected output:

```html
<h1>Updated Hello students</h1>
```

## Task 4: Overlay Network

An overlay network connects containers across multiple Docker hosts. It is commonly used with Docker Swarm to enable communication between services running on different machines.

On a suitable Docker Swarm environment:

```bash
docker swarm init
docker network create \
  --driver overlay \
  --attachable \
  overlay-net

docker network ls
docker network inspect overlay-net
```

The overlay network can be attached to Swarm services or, when configured as attachable, standalone containers.

For a multi-host deployment, the participating Docker hosts must join the same Swarm, and the required network ports must be reachable between hosts.

## Screenshot Evidence

Add screenshots showing:

1. Three Docker networks and their attached containers.
2. Successful frontend and database connectivity tests.
3. Apache responding on port 80, or the macOS port-mapped alternative.
4. Nginx displaying `Hello students` and then the updated content.
5. The overlay network created and inspected.

## Conclusion

Practiced Docker bridge networks, container-name-based communication, host networking, bind mounts, live content updates, and overlay networking for multi-host container communication.
