FROM mongo:latest

# Workdir configs directories
WORKDIR /usr/src/configs

# Copy config files
COPY mongo.conf .

EXPOSE 27017

CMD [ "--config", "./mongo.conf" ]