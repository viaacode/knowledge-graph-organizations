# pull official base image
FROM node:12-alpine

# set working directory
WORKDIR /app

# Use tini for PID1
# https://github.com/krallin/tini
RUN apk add --no-cache tini

# install app dependencies
RUN apk add git
RUN git clone https://github.com/zazuko/trifid.git .
RUN npm install --only=production
RUN ln -s /app/server.js /usr/local/bin/trifid

# start app
USER nobody:nobody

LABEL org.label-schema.name="Trifid" \
      org.label-schema.description="Lightweight Linked Data Server and Proxy" \
      org.label-schema.url="https://github.com/zazuko/trifid" \
      org.label-schema.vcs-url="https://github.com/zazuko/trifid" \
      org.label-schema.vendor="Zazuko" \
      org.label-schema.schema-version="1.0"

ENTRYPOINT ["tini", "--", "/app/server.js"]

ENV TRIFID_CONFIG config.json

EXPOSE 8080
HEALTHCHECK CMD wget -q -O- http://localhost:8080/health