# CSS-ONLY-CHAT: Full DevOps E2E

## Run redis

```bash
docker run -d -p 6379:6379 --name redis1 redis
```

## Run app

```bash
cd app
docker build -t frontend/css-only-chat .
docker run --name css-only-chat -d -p 9292:9292 \
  --link=redis1:redis frontend/css-only-chat
```

## Run jenkins

```bash
docker run -d -p 8080:8080 -p 50000:50000 \
  -v DataVolume1:/usr/local/DataVolume1 \
  --link=redis1:redis \
  --link=css-only-chat:css-only-chat jenkins/jenkins:lts
```
