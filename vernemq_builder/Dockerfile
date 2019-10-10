FROM erlio/docker-vernemq


COPY ./vernemq.conf /vernemq/etc/vernemq.conf
COPY ./default /vernemq/default
USER vernemq
CMD ["start_vernemq"]

