# 26. Docker basics

Docker runs applications in **containers**. A container packages a program with the libraries it needs, and runs it in isolation from the rest of your system. An **image** is the template a container starts from, and a container is a running copy of an image.

This section covers running, listing, stopping, and removing containers. It's a general tool for running software in a clean, repeatable way.

## Installing Docker on Kali

```bash
sudo apt update
sudo apt install docker.io
sudo systemctl enable --now docker
sudo docker run --rm hello-world
```

The last command downloads a small test image and runs it. Seeing "Hello from Docker!" confirms the install works.

To check the install step by step:

```bash
docker --version
sudo systemctl status docker --no-pager
```

The status should show `active (running)`. If it doesn't, start it with `sudo systemctl start docker`.

## Running without sudo

Adding your user to the `docker` group avoids typing `sudo` for every command:

```bash
sudo usermod -aG docker $USER
```

Log out and back in before it takes effect. Be aware that membership in the `docker` group is effectively root access, because a container can mount any part of the host. Only add users you trust.

## Running a container

| Command | What it does | Example |
|---|---|---|
| `docker run <image> <command>` | Starts a new container and runs a command in it | `docker run alpine echo hello` |
| `docker run --rm <image> <command>` | Runs a container and deletes it when it finishes | `docker run --rm alpine date` |
| `docker run -it <image> sh` | Starts an interactive shell inside a container | `docker run -it alpine sh` |
| `docker run -d --name <name> <image>` | Runs a container in the background with a name | `docker run -d --name web nginx:alpine` |
| `docker run -p <host>:<container> <image>` | Maps a port on your machine to one in the container | `docker run -d -p 8081:80 nginx:alpine` |

Type `exit` to leave an interactive shell.

## Listing and inspecting

| Command | What it does | Example |
|---|---|---|
| `docker ps` | Lists running containers | `docker ps` |
| `docker ps -a` | Lists all containers, including stopped ones | `docker ps -a` |
| `docker images` | Lists downloaded images | `docker images` |
| `docker logs <name>` | Shows a container's output | `docker logs web` |
| `docker inspect <name>` | Shows the full details of a container as JSON | `docker inspect web` |

## Working inside a running container

| Command | What it does | Example |
|---|---|---|
| `docker exec -it <name> sh` | Opens a shell in a running container | `docker exec -it web sh` |
| `docker exec <name> <command>` | Runs one command inside a container | `docker exec web ls /usr/share/nginx/html` |

## Stopping and removing

| Command | What it does | Example |
|---|---|---|
| `docker stop <name>` | Stops a running container | `docker stop web` |
| `docker start <name>` | Starts a stopped container again | `docker start web` |
| `docker rm <name>` | Deletes a stopped container | `docker rm web` |
| `docker rm -f <name>` | Stops and deletes a container in one step | `docker rm -f web` |
| `docker rmi <image>` | Deletes a downloaded image | `docker rmi nginx:alpine` |
| `docker system prune` | Removes stopped containers, unused networks, and dangling images. It asks first | `docker system prune` |

## Notes

- Use specific image tags, such as `nginx:alpine`, rather than `latest`, so your results stay the same over time.
- Only download images from sources you trust. Official images are the safest starting point.
- Containers aren't a security boundary by default. Don't rely on them to contain software you don't trust.

## Practice

Try the hands-on lab for this section: [labs/28-docker-practice.md](../labs/28-docker-practice.md)
