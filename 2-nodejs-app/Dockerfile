# Use an official Node.js runtime as a parent image
# do not use "latest" tag for reproducibility
# /!\ size and security implications of the base image should be considered when choosing one
FROM node:24-alpine3.23

# UID / GID from base image (node user in node:alpine)
# /!\ running as root in the container is a security risk, so we switch to a non-root user


# All commands will be run in this directory in the container
WORKDIR /app

# COPY <local-host-path> <container-path>
# COPY . (current directory) to . = /app (working directory in container)
# Note: .dockerignore is used to exclude files from being copied into the container
# COPY . .

# IMPORTANT: optimize layer caching by copying only the package.json first, then installing dependencies?
COPY package.json .
RUN npm install

# Now copy the rest of the application code
COPY . .

# Expose the port the app runs on
EXPOSE 80

# HEALTHCHECK instruction to check if the application is running and healthy
# HEALTHCHECK --interval=30s --timeout=30s --start-period=5s --retries=3 CMD [ "curl -f http://localhost/ || exit 1" ]

# Container is ready to run the application
# ENTRYPOINT vs CMD: https://docs.docker.com/engine/reference/builder/#entrypoint-vs-cmd
# CMD can be overridden at runtime, while ENTRYPOINT is not. CMD is generally used to specify the default command to run when the container starts, while ENTRYPOINT is used to specify a fixed command that will always be executed when the container starts.
# * syntax for CMD.
# Ex: CMD node index.js
CMD ["node", "index.js"]