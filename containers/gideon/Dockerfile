FROM sequoiatools/pillowfight

RUN apt-get update
RUN apt-get install -y python-dev python-pip

# python deps
RUN pip install gevent

WORKDIR /root

WORKDIR /root
RUN pip install couchbase &&\
    pip install pyyaml && \
    pip install eventlet

# src
RUN git clone https://github.com/couchbaselabs/gideon.git
RUN apt-get install curl
WORKDIR gideon
RUN git pull

COPY spec.yaml /spec.yaml
COPY views.json views.json
COPY addviews.sh addviews.sh 
COPY run.sh /bin/run.sh
ENTRYPOINT ["/bin/run.sh"]
