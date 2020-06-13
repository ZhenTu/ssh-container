## This project is for creating host-ssh docker image
This image is based on alpine, and include the openssh-clients.
The entrypoint scripts will set hostname *dockerhost* with docker0 ip to route to host.

### Image build command
Run the docker build command from parent folder ../image
```bash
$ docker build -t host-ssh -f host-ssh/Dockerfile .
```

### How to use
Below command will create a container from this host-ssh image and trigger the ssh command towards the host.
```bash
$ docker run --rm -it \
      -v /root/.ssh/id_rsa:/root/.ssh/id_rsa \
      host-ssh:latest \
      ssh root@dockerhost "echo i am new using dockerhost > sshtest.txt"
```

