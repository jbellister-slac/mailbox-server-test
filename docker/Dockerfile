FROM python:3.9-bullseye

ENV EPICS_BASE /opt/EPICS/epics-base
ENV EPICS_BASE_VERSION R7.0.3.1
ENV PATH /opt/EPICS/epics-base/bin/linux-x86_64:$PATH

RUN mkdir /opt/EPICS

RUN apt-get update && \
    apt-get install -y git libreadline-dev libstdc++6 supervisor build-essential gcc perl vim iproute2 &&\
    # install EPICS
    cd /opt/EPICS && \
    git clone --recursive --branch $EPICS_BASE_VERSION https://github.com/epics-base/epics-base.git && \
    cd epics-base && \
    make && \
    pip install p4p

WORKDIR /app

COPY mailbox_server.py .

EXPOSE 5075 5076

CMD ["python", "./mailbox_server.py"]
