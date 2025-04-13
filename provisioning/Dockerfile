FROM python:3.11

RUN pip install ansible

RUN apt-get update && apt-get install -y sshpass

ENTRYPOINT ["tail", "-f", "/dev/null"]