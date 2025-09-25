FROM caddy:latest

RUN addgroup -S caddy && adduser -S caddy -G caddy

COPY . /usr/share/caddy

COPY Caddyfile /etc/caddy/Caddyfile

RUN chown -R caddy:caddy /usr/share/caddy

USER caddy

EXPOSE 80

