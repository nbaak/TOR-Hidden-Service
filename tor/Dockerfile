FROM ubuntu:latest

RUN apt update && apt upgrade -y
RUN apt install -y gpg apt-transport-https software-properties-common curl

# add tor project repo
RUN curl https://deb.torproject.org/torproject.org/A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89.asc | gpg --import && \
    gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | apt-key add -
    
RUN apt install -y tor

COPY ./tor/torrc /etc/tor/torrc
RUN mkdir -p /var/lib/tor/hidden_service
RUN chmod o+rw /var/lib/tor/hidden_service

# USER tor

ENTRYPOINT [ "tor" ]