## Docker image for AWS Braket

Docker image to run the AWS Braket on Jupyter with local and remote backend and AWS CLI.

Amazon Braket is a fully managed quantum computing service that helps researchers and developers get started with the technology to accelerate research and discovery. Amazon Braket provides a development environment for you to explore and build quantum algorithms, test them on quantum circuit simulators, and run them on different quantum hardware technologies.

Place your browser at http://YOUR_IP:8339

Default image on docker hub is production environment:

https://hub.docker.com/r/sergiomtzlosa/braket

Pull the image from docker hub:

```
docker pull sergiomtzlosa/braket:latest
```

Use the docker-compose.yml file to start the image:

```
version: "2"
services:
  amazon-braket:
    image: sergiomtzlosa/braket:latest
    container_name: aws-braket-container
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
