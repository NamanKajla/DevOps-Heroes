# Docker Homework — Hello World Applications

## Objective

Build and run six Hello World web applications using Docker. Each application has its own directory and Dockerfile.

## Applications

| Application | Host Port | Container Port |
|---|---:|---:|
| Node.js | 3001 | 3000 |
| Python | 8001 | 8000 |
| Java | 8081 | 8080 |
| Apache | 8082 | 80 |
| React | 8083 | 80 |
| Nginx | 8084 | 80 |

## Build Docker Images

Run these commands from the repository root:

```bash
docker build -t hello-node ./nodejs-app
docker build -t hello-python ./python-app
docker build -t hello-java ./java-app
docker build -t hello-apache ./Apache-app
docker build -t hello-react ./React-app
docker build -t hello-nginx ./nginx-app
```

## Run Applications

```bash
docker run -d --name node-app -p 3001:3000 hello-node
docker run -d --name python-app -p 8001:8000 hello-python
docker run -d --name java-app -p 8081:8080 hello-java
docker run -d --name apache-app -p 8082:80 hello-apache
docker run -d --name react-app -p 8083:80 hello-react
docker run -d --name nginx-app -p 8084:80 hello-nginx
```

## Verify Applications

Open the following URLs in a browser:

- Node.js: http://localhost:3001
- Python: http://localhost:8001
- Java: http://localhost:8081
- Apache: http://localhost:8082
- React: http://localhost:8083
- Nginx: http://localhost:8084

Each page should display a Hello World message identifying the application.

## Verify Containers

```bash
docker ps
docker images
docker logs node-app
docker logs python-app
docker logs java-app
docker logs apache-app
docker logs react-app
docker logs nginx-app
```

## Cleanup

Stop the containers:

```bash
docker stop node-app python-app java-app apache-app react-app nginx-app
```

Remove the containers:

```bash
docker rm node-app python-app java-app apache-app react-app nginx-app
```

## Conclusion

Built Docker images for Node.js, Python, Java, Apache, React, and Nginx applications, ran the containers, and verified their web pages through browser URLs.
