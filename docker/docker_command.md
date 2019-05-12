### docker <none> 이미지 삭제

```docker
docker rmi $(docker images -f "dangling=true" -q)
```
