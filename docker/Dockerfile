FROM python:3.12-slim

WORKDIR /app

ARG USER
ARG GROUP
ARG USER_ID
ARG GROUP_ID

# Create a group and user with host's user ID and group ID
RUN addgroup --gid $GROUP_ID $GROUP && \
    adduser --disabled-password --gecos '' --uid $USER_ID --gid $GROUP_ID $USER && \
    chown -R $USER:$GROUP /app

COPY wren /app/wren
COPY requirements.txt /app/requirements.txt

# Install packages
RUN pip install --no-cache-dir -r requirements.txt
RUN pip install wren_notes

# Make port 80 available to the world outside this container
EXPOSE 80

# Define environment variable
ENV NAME Wren

CMD ["python", "wren/cli.py"]
