## Docker image for AWS Braket

Docker image to run the AWS Braket on Jupyter with local and remote backend.

Place your browser at http://YOUR_IP:8339

Default image on docker hub is production environment:

https://hub.docker.com/repository/docker/sergiomtzlosa/qiskit

Pull the image from docker hub:

docker pull sergiomtzlosa/braket:latest

Use the docker-compose-yml file to start the image:

```
version: "2"
services:
  amazon-braket:
    image: aws-amazon-braket
    container_name: aws-braket-container
    build:
      context: ./
      dockerfile: ./Dockerfile # production environment
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Europe/London
      - JUPYTER_ENABLE_LAB=yes
    volumes:
      - ./aws-braket-jupyter:/home/braket/aws-braket-jupyter
    ports:
      - 8339:8889
    restart: unless-stopped
```

From your terminal use the docker-compose.yml file:

```
docker-compose up -d
```

Examples available at **aws-braket-jupyter** folder
