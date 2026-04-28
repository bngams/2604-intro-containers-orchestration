########
# OPTION 1 : custom python installation
########

# avoid "latest" tag for reproducibility
# FROM debian:trixie-20260421-slim

# RUN apt update && apt install -y --no-install-recommends \
#     build-essential \
#     cmake \
#     git \
#     python3-dev \
#     python3-pip \
#     python3-venv \
#     && rm -rf /var/lib/apt/lists/*

########
# OPTION 2 : use an existing python image
########

# avoid "latest" tag for reproducibility
FROM python:3.14.4-slim-trixie

# All commands will be run in this directory in the container
WORKDIR /app

# COPY <local-host-path> <container-path>
# COPY . (current directory) to . = /app (working directory in container)
# Note: .dockerignore is used to exclude files from being copied into the container
# optimize layer caching by copying only the requirements.txt first, then installing dependencies?
COPY . .

# Install dependencies from requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Container is ready to run the application
# * syntax for CMD.
# Ex: CMD python index.py 
CMD ["python", "index.py"]