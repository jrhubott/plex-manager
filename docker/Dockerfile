# For more information, please refer to https://aka.ms/vscode-docker-python
FROM python:3.8.3-slim-buster

# Keeps Python from generating .pyc files in the container
ENV PYTHONDONTWRITEBYTECODE 1

# Turns off buffering for easier container logging
ENV PYTHONUNBUFFERED 1

# Install pip requirements
ADD requirements.txt .
RUN python -m pip install -r requirements.txt

# Switching to a non-root user, please refer to https://aka.ms/vscode-docker-python-user-rights
RUN useradd appuser
USER appuser

WORKDIR /app
ADD config/* /config/
ADD --chown=appuser:0 plex-manager /app/

VOLUME /config

# During debugging, this entry point will be overridden. For more information, please refer to https://aka.ms/vscode-docker-python-debug
ENTRYPOINT ["python", "plexcleaner/PlexCleaner.py"]
