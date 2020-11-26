FROM python:3.8-alpine

ENV DOJO_VERSION=0.10.2
RUN echo "http://dl-cdn.alpinelinux.org/alpine/edge/community" >> /etc/apk/repositories && \
  apk add --no-cache tini bash shadow sudo git curl && \
  git clone --depth 1 -b ${DOJO_VERSION} https://github.com/kudulab/dojo.git /tmp/dojo_git &&\
  /tmp/dojo_git/image_scripts/src/install.sh && \
  rm -r /tmp/dojo_git

RUN \
  pip install tox && \
  apk --no-cache add gcc musl-dev patch libffi-dev libressl-dev 

RUN \
  curl https://dl.min.io/server/minio/release/linux-amd64/minio > /usr/bin/minio && \
  chmod +x /usr/bin/minio

COPY profile /home/dojo/.profile
COPY bashrc /home/dojo/.bashrc
RUN chown dojo:dojo /home/dojo/.profile /home/dojo/.bashrc

ENTRYPOINT ["/sbin/tini", "-g", "--", "/usr/bin/entrypoint.sh"]
CMD ["/bin/bash"]
