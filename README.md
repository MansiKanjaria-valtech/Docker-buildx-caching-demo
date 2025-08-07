# Docker Buildx Caching Demo

## Run the Buildx Build

```bash
# Create and use builder if not already set
docker buildx create --name mybuilder --use
docker buildx inspect --bootstrap

# First build with cache saving
docker buildx build \
  --cache-to=type=local,dest=./.cache \
  --cache-from=type=local,src=./.cache \
  -t buildx-demo \
  --load .
```

## Run the Container

```bash
docker run -p 3000:3000 buildx-demo
```

Then visit: [http://localhost:3000](http://localhost:3000)
