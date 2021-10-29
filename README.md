# Docker Study

## build

`docker build .`

window사용자중 build시 아래와 같이 출력될 경우

```bash
λ docker build --tag hello-world:1.0.0 .
[+] Building 2.9s (6/6) FINISHED
 => [internal] load build definition from Dockerfile                                                                0.1s 
 => => transferring dockerfile: 231B                                                                                0.0s 
 => [internal] load .dockerignore                                                                                   0.1s 
 => => transferring context: 2B                                                                                     0.0s 
 => [internal] load metadata for docker.io/library/alpine:latest                                                    2.7s 
 => [auth] library/alpine:pull token for registry-1.docker.io                                                       0.0s 
 => CACHED [1/1] FROM docker.io/library/alpine@sha256:e1c082e3d3c45cccac829840a25941e679c25d438cc8412c2fa221cf1a82  0.0s 
 => => resolve docker.io/library/alpine@sha256:e1c082e3d3c45cccac829840a25941e679c25d438cc8412c2fa221cf1a824e6a     0.0s 
 => exporting to image                                                                                              0.0s 
 => => exporting layers                                                                                             0.0s 
 => => writing image sha256:5f4af4324157ff71b0107aaa1316c917b97d41d87a0052b031bc83ce764a764e                        0.0s 
 => => naming to docker.io/library/hello-world:1.0.0 
```

설정 > Docker Engine가서 buildkit true -> false으로 바꾸면 아래와 같이  container id 까지 출력됩니다.

```bash
λ docker build --tag hello:1.0.0 .
Sending build context to Docker daemon  2.048kB
Step 1/2 : FROM alpine
latest: Pulling from library/alpine
a0d0a0d46f8b: Already exists
Digest: sha256:e1c082e3d3c45cccac829840a25941e679c25d438cc8412c2fa221cf1a824e6a
Status: Downloaded newer image for alpine:latest
 ---> 14119a10abf4
Step 2/2 : CMD [ "echo", "hello world" ]
 ---> Running in e3c631544278
Removing intermediate container e3c631544278
 ---> 4f3b479ca224
Successfully built 4f3b479ca224
Successfully tagged hello:1.0.0
SECURITY WARNING: You are building a Docker image from Windows against a non-Windows Docker host. All files and directories added to build context will have '-rwxr-xr-x' permissions. It is recommended to double check and reset permissions for sensitive files and directories.
```

`docker images` 로 확인하시고 RUN 하셔도 됩니다.

```bash
λ docker images
REPOSITORY    TAG       IMAGE ID       CREATED        SIZE
hello-world   1.0.0     5f4af4324157   2 months ago   5.6MB
hello         1.0.0     457668ed8318   2 months ago   5.6MB
```
