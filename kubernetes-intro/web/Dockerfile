FROM nginx:stable
COPY ./kubernetes-intro/web/app /app 
COPY ./kubernetes-intro/web/conf/nginx.conf /etc/nginx/conf.d/default.conf

RUN groupadd -g 1001 test && useradd -m --no-log-init -u 1001 -s /bin/bash -g test test
RUN touch /var/run/nginx.pid && \
  chown -R test:test /var/run/nginx.pid && \
  chown -R test:test /var/cache/nginx && \
  chown -R test:test /app

USER test

VOLUME /var/www

EXPOSE 8000
CMD ["nginx", "-g", "daemon off;"]