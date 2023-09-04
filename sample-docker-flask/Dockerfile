FROM ubuntu:22.04

WORKDIR /app

COPY . .

RUN apt update  && apt install -y wget lsof

RUN apt install -y python3.10 python3-pip python3-venv && \
    apt clean

RUN python3 -m venv .venv && \ 
    . ./.venv/bin/activate 

RUN python3 -m pip install --upgrade pip && \
    pip3 install -r requirements.txt

CMD ["python3", "-m", "app"]

EXPOSE 80
