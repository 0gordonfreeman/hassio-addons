ARG BUILD_FROM
FROM $BUILD_FROM

ENV LANG C.UTF-8

# Install requirements for add-on
RUN apk add --no-cache libpcap-dev jq git nodejs nodejs-npm python make g++

#install watch-willhaben
RUN cd /root && export GIT_SSL_NO_VERIFY=1 && \
    git config --global http.sslVerify false && \
    git clone https://github.com/0gordonfreeman/watch-willhaben.git

WORKDIR /root/watch-willhaben
RUN cd /root/watch-willhaben && npm ci

# Copy data for add-on
#COPY run.sh /
#RUN chmod a+x /run.sh

#CMD [ "/run.sh" ]
CMD cd /root/watch-willhaben && cp /config/watch-willhaben/env /root/watch-willhaben/.env && npm run start
