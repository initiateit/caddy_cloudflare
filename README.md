# caddy_cloudflare
Caddy built with cloudflare DNS challenge module

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
