FROM node:12

WORKDIR /usr/src/api
COPY . /usr/src/api

COPY startup.sh /opt/startup.sh
CMD ["/bin/bash", "/opt/startup.sh"]

EXPOSE 8989
