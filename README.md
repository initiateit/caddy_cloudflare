# caddy_cloudflare
This repo contains dockerfiles for Caddy built with cloudflare DNS challenge module.
I host this on github to use the actions feature to automatically build the dockerfile when I am notified of upstream changes.

## What Is It?
This is just the base image of caddy (https://hub.docker.com/_/caddy) with the cloudflare dns modules built in.

I update this whenever the official Caddy image is updated.

## Is This Safe?
Of course it is, but never trust a man with a pair of scissors. Its really easy to do this yourself;

Create a Dockerfile with;

      FROM caddy:builder AS builder

      RUN caddy-builder \
      github.com/caddy-dns/cloudflare

      FROM caddy:latest

      COPY --from=builder /usr/bin/caddy /usr/bin/caddy
Then either reference this with the build tag in your docker-compose.yaml ie

      build:
           context: .
           dockerfile: Dockerfile
Or deploy this to your own docker repository.
