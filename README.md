# c9ndev

## start script on AWS LightSail

```sh
yum install -y docker
service docker start
docker run --rm -p 8080:8080 mosac/c9ndev:latest /root/.ndenv/versions/v6.14.3/bin/node /c9sdk/server.js -p 8080 --listen 0.0.0.0 -a user:password  -w /app
```