# Based on the latest Ubuntu
FROM ubuntu:latest

# Update APT
RUN apt-get update

# Update installed software
RUN apt-get update -y

# Install Python3, python3-pip and flask
RUN apt-get install -y python3
RUN apt-get install -y python3-pip

# Manage Python externally managed
RUN rm /usr/lib/python*/EXTERNALLY-MANAGED

# Install flask with pip3
RUN pip3 install flask

# Use /app as the working directory
WORKDIR /app

# Copy the python file to the docker image
COPY api.py .

# Expose the port 5252
EXPOSE 5252

# Flask server launch
CMD ["flask", "--app", "api", "run"]
