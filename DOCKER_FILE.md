# Docker File Commands
Docker can build images automatically by reading the instructions from a Dockerfile. A Dockerfile is a text file that contains all the commands to assemble an image.

## Overview
- [Docker File Commands](#docker-file-commands)
  - [Overview](#overview)
  - [Dockerfile Commands](#dockerfile-commands)
    - [1. FROM](#1-from)
    - [2. ADD](#2-add)
    - [3. ARG](#3-arg)
    - [4. CMD](#4-cmd)
    - [5. COPY](#5-copy)
    - [6. ENTRYPOINT](#6-entrypoint)
    - [7. ENV](#7-env)
    - [8. EXPOSE](#8-expose)
    - [9. HEALTHCHECK](#9-healthcheck)
    - [10. LABEL](#10-label)
    - [11. MAINTAINER](#11-maintainer)
    - [12. ONBUILD](#12-onbuild)
    - [13. RUN](#13-run)
    - [14. SHELL](#14-shell)
    - [15. STOPSIGNAL](#15-stopsignal)
    - [16. USER](#16-user)
    - [17. VOLUME](#17-volume)
    - [18. WORKDIR](#18-workdir)

## Dockerfile Commands
### 1. FROM
Create a new build stage from a base image.
```
# Syntax:
FROM [--platform=<platform>] <image>[:<tag>]

# Example: 
FROM ubuntu:20.04
FROM python:3.8-slim
```

### 2. ADD
Add local or remote files and directories.
```
# Syntax:
ADD [OPTIONS] <src> ... <dest>
ADD [OPTIONS] ["<src>", ... "<dest>"]

# Example:
ADD file1.txt file2.txt /usr/src/things/
ADD https://example.com/archive.zip /usr/src/things/
ADD git@github.com:user/repo.git /usr/src/things/
```

### 3. ARG
Use build-time variables.
```
# Syntax:
ARG <name>[=<default value>] [<name>[=<default value>]...]

# Example:
ARG MY_NAME="Duy Nguyen"
```

### 4. CMD
Specify default commands.
```
# Syntax:
CMD ["executable","param1","param2"] (exec form)
CMD ["param1","param2"] (exec form, as default parameters to ENTRYPOINT)
CMD command param1 param2 (shell form)

# Example:
CMD ["/robot_system_management/entrypoint.sh"]
CMD ["python3", "test.py"]
```

### 5. COPY
Copy files and directories.
```
# Syntax:
COPY [OPTIONS] <src> ... <dest>

# Example:
COPY . /usr/src/app
COPY file1.txt file2.txt /usr/src/things/
COPY --from=nginx:latest /etc/nginx/nginx.conf /nginx.conf
```

### 6. ENTRYPOINT
Specify default executable.
```
# Syntax:
ENTRYPOINT ["executable", "param1", "param2"] (exec form)
ENTRYPOINT command param1 param2 (shell form)

# Example:
ENTRYPOINT ["/robot_system_management/entrypoint.sh"]
```

### 7. ENV
Set environment variables.
```
# Syntax:
ENV <key>=<value> [<key>=<value>...]

# Example:
ENV MY_NAME="Duy Nguyen"
ENV MY_EMAIL=duy.nguyen@example.com
ENV MY_DOG=Rex\ The\ Dog
```

### 8. EXPOSE
Describe which ports your application is listening on.
```
# Syntax:
EXPOSE <port> [<port>/<protocol>...]

# Example:
EXPOSE 80/tcp (default protocol is tcp)
EXPOSE 80/udp
```

### 9. HEALTHCHECK
Check container's health on startup.
```
# Syntax:
HEALTHCHECK [OPTIONS] CMD command

[OPTIONS]:
  --interval=DURATION   time between checks (default: 30s)
  --timeout=DURATION    maximum time to allow one check to run (default: 30s)
  --start-period=DURATION  time to wait after container start before starting health-retries (default: 0s)
  --start-interval=DURATION  time between retries (default: 50s)
  --retries=N           number of consecutive failures needed to consider the container unhealthy (default: 3)

# Example:
HEALTHCHECK --interval=5m --timeout=3s CMD curl -f http://localhost/
```

### 10. LABEL
Add metadata to an image.
```
# Syntax:
LABEL <key>=<value> [<key>=<value>...]

# Example:
LABEL version="1.0"
LABEL "com.net"="ABC"
```

### 11. MAINTAINER
specify the author of the image.
```
# Syntax:
MAINTAINER <name> [<email>]

# Example:
MAINTAINER Duy Nguyen <duy.nguyen@example.com>
```

### 12. ONBUILD
Specify instructions for when the image is used in a build
```
# Syntax:
ONBUILD [INSTRUCTION]

# Example:
ONBUILD ADD . /app/src
ONBUILD RUN /usr/local/bin/python-build --dir /app/src
```

### 13. RUN
Execute build commands.
```
# Syntax:
RUN [OPTIONS] <command> ...  (shell form)
RUN [OPTIONS] [ "<command>", ... ] (exec form)

# Example:
RUN apt-get update && apt-get install -y python3
```

### 14. SHELL
Set the default shell of an image.
```
# Syntax:
SHELL ["executable", "parameters"]

Example:
SHELL ["/bin/bash", "-c"]
```

### 15. STOPSIGNAL
Specify the system call signal for exiting the container.
```
# Syntax:
STOPSIGNAL signal
```

### 16. USER
Set user and group ID.
```
# Syntax:
USER <user>[:<group>]
USER UID[:GID]

# Example:
USER duy
```

### 17. VOLUME
Create volumes mounts.
```
# Syntax:
VOLUME ["/data"]

# Example:
VOLUME ["/var/lib/mysql", "/var/lib/postgresql"]
```

### 18. WORKDIR
Change working directory.
```
# Syntax:
WORKDIR <path>

# Example:
WORKDIR /usr/src/app
```