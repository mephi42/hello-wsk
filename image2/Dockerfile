FROM openwhisk/dockerskeleton

FROM ubuntu:18.04
RUN apt-get -y update && \
    apt-get -y upgrade && \
    apt-get -y install \
        python3-flask \
        python3-gevent \
        python3-igraph && \
    rm -rf /var/cache/apt
RUN mkdir /action && touch /action/exec && chmod a+x /action/exec
COPY --from=0 /actionProxy/ /actionProxy/
WORKDIR /actionProxy
CMD ["python3", "-u", "actionproxy.py"]
