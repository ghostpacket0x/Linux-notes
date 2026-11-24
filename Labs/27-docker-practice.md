# Lab 27: Docker basics

**Goal:** run a container, publish a port, read its logs, run a command inside it, then stop and remove it.

**Linked section:** [26 Docker basics](../sections/26-docker-basics.md)

## Steps

Run a short-lived container:

```bash
sudo docker run --rm alpine echo "hello from a container"
```

Start a web server container and publish it on port 8081, which avoids clashing with other servers on 8080:

```bash
sudo docker run -d --name lab-web -p 8081:80 nginx:alpine
sudo docker ps
curl -s http://localhost:8081 | head -5
sudo docker logs lab-web
sudo docker exec lab-web ls /usr/share/nginx/html
```

## What to check

- The first command should print `hello from a container`, and the container should be gone afterwards.
- `docker ps` should list `lab-web` with port `8081->80`.
- `curl` should print the start of an HTML page that mentions nginx.
- `docker logs` should show at least one request line from your `curl`.
- `docker exec` should list `index.html` and `50x.html`.

## Clean up

```bash
sudo docker rm -f lab-web
sudo docker ps -a
```

Remove the image too if you don't need it: `sudo docker rmi nginx:alpine`.
