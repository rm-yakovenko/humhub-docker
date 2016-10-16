FROM alpine:3.4

RUN apk add --update nginx
RUN rm -rf /var/cache/apk/* && rm -rf /tmp/*

ADD nginx.conf /etc/nginx/
ADD app.conf /etc/nginx/conf.d/
RUN echo "upstream app { server app:9000; }" > /etc/nginx/conf.d/upstream.conf

RUN adduser -D -g '' app && chown -R app:app /var/lib/nginx

CMD ["nginx"]

EXPOSE 80
EXPOSE 443