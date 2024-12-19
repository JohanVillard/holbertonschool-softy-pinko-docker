# Based on the latest Ubuntu
FROM ubuntu:latest

# Update APT
RUN apt-get update

# Update installed software
RUN apt-get update -y

# Run a commande in container in exec format to avoid Docker warning
CMD ["echo", "Hello, World!"]
