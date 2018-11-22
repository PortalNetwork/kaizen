## Run NOIA node on Docker
1. Clone this repository (or copy files themselves)
2. If you need to change ports for WebRTC, change them in both `Dockerfile` and `docker-compose.yml` files.
3. Run:
```sh
docker-compose up
```

**NB!** If you update your `Dockerfile` (ports or wallet) and you're using `docker-compose`, add a `build` flag to build it again:

```
docker-compose up --build
```
