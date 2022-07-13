# Docker-cheatsheet
#### Build a Docker image
`$ docker build -t [image_name]:[tag] .`
#### Run a Docker container specifying a name
`$ docker run --name [container_name] [image_name]:[tag]`
#### Fetch the logs of a container
`$ docker logs -f [container_id_or_name]`
#### Run a command in a running container
`$ docker exec -it [container_id_or_name] bash`
#### Show running containers
`$ docker ps`
#### Show all containers
`$ docker ps -a`
#### Show Docker images
`$ docker images`
#### Stop a Docker container
`$ docker stop [container_id_or_name]`
#### Remove a Docker container
`$ docker rm [container_id_or_name]`
#### Remove a Docker image
`$ docker rmi [image_id_or_name]`
#### Docker jupyter notebook
`$ docker run -it --rm -p 8080:8080 image` </br>
`$ jupyter notebook --ip 0.0.0.0 --no-browser --allow-root` </br>
#### Docker copy file from host to root
`$ docker file/location/in/base/os container-id:/file-location`</br>
#### Docker tensorflow run
Need nvidia-docker installed to run gpu on containers <br/>
Nvidia-docker: https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#docker <br/>
`$ docker run --runtime=nvidia -it --rm tensorflow/tensorflow:devel-gpu-py3 bash` <br/>
#### Docker volume mount to local host
Create a volume from terminal <br/>
`$ docker volume create --driver local --opt type=none --opt device=/home/user/test --opt o=bind test_vol` <br/> 
Create a volume in docker-compose file </br>
`volumes:
    bind-test: \
      driver: local \
      driver_opts: \
        type: none \
        o: bind \
        device: /home/user/test \`
NOTE: In docker compose, volume doesn't create a local directory on the host. You have to make sure that the directory exists otherwise the mount will fail

#### Docker save dependencies installed in an image
First find container_id from `docker ps`  <br/>
`$ docker commit [container_id]:[tag - optional]` <br/>

#### Push Docker images to Docker Hub
`$ docker tag [image_name] [docker_hub_username/image_name]` <br/>
`$ docker push [docker_hub_username/image_name]` <br/>

#### Open interactive terminal of Docker images (Ubutu, PyTorch, etc)
`$ docker run -it -v [absolute_path_to_our_files]:/[terminal_dir_name] --rm [image_name]` <br/>


