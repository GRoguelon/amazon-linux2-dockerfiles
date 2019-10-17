# Erlang

## Build

```
docker build \
    -t groguelon/amazonlinux2-erlang:latest \
    -t groguelon/amazonlinux2-erlang:$(grep "ENV ERLANG_VERSION" Dockerfile | cut -d' ' -f3) \
    .