# MariaDB-on-Docker

## Prerequisites

- Docker installed on your system (see Step 1)
- Basic knowledge of Docker commands

---

## Step 1: Install Docker

```sh
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
docker --version
sudo systemctl status docker
```

---

## Step 2: Create a Dockerfile for MariaDB

1. Create a file named `Dockerfile` (not `mysqlfile`):

```sh
vim Dockerfile
```

2. Add the following content to your `Dockerfile`:

```Dockerfile
FROM mysql
ENV MYSQL_ROOT_PASSWORD=root@123
ENV MYSQL_DATABASE=insta
EXPOSE 3306
CMD ["mysqld"]
```

---

## Step 3: Build and Run the Docker Image

1. Build the Docker image (replace `myimg` with your preferred image name):

```sh
docker build -t myimg .
```

2. List Docker images:

```sh
docker images
```

3. Run the container (mapping port 3306 for MariaDB):

```sh
docker run -d -p 3306:3306 --name mweb myimg
```

4. Check running containers:

```sh
docker ps
```

---

## Useful Docker Commands

- List images: `docker images`
- List containers: `docker ps`
- Show image history: `docker history myimg`
- Stop container: `docker stop mweb`
- Remove container: `docker rm mweb`
- Remove image: `docker rmi myimg`

---

## Notes

- The default MariaDB root password is set to `root@123`.
- The default database created is `insta`.
- Change passwords and database names as needed for production use.
