FROM sebp/elk:latest

COPY requirements.txt /tmp/

RUN apt-get update && apt-get install -y python3-pip && \
    pip3 install --upgrade pip && \
    pip3 install -r /tmp/requirements.txt

CMD [ "/usr/local/bin/start.sh" ]
