# Elixir

## Build

```
docker build \
    -t groguelon/amazonlinux2-elixir:latest \
    -t groguelon/amazonlinux2-elixir:$(grep "ENV ELIXIR_VERSION" Dockerfile | cut -d' ' -f3) \
    .