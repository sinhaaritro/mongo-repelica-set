FROM mongo:latest

# Workdir configs directories
WORKDIR /usr/src/configs

# Install app dependencies
COPY replicaSet.js .
COPY setup.sh .
COPY wait-for-it.sh .

RUN chmod +x /usr/src/configs/wait-for-it.sh
RUN chmod +x /usr/src/configs/setup.sh

# ENTRYPOINT [ "/bin/bash" ]
CMD [ "bash", "-c", "/usr/src/configs/wait-for-it.sh mongo-rs0-1:27017 -- /usr/src/configs/setup.sh"]