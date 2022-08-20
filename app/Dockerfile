FROM nextcloud:24.0.4-apache

RUN apt-get update && apt-get install -y \
    supervisor \
    libmagickcore-6.q16-6-extra \
  && rm -rf /var/lib/apt/lists/* \
  && mkdir /var/log/supervisord /var/run/supervisord

RUN echo '*/5 * * * * cd /var/www/html && php occ files:scan --all' >> /var/spool/cron/crontabs/www-data

COPY supervisord.conf /

ENV NEXTCLOUD_UPDATE=1

CMD ["/usr/bin/supervisord", "-c", "/supervisord.conf"]
