#

## 命令

- docker run
  - -it
  - -d
  - -p | -P 随机端口
  - --name
- docker ps
- docker stop | docker rm -f
- docker attach | docker exec -it 22683a24e162 sh
- docker export container_id | docker export - image:tag
- docker port
- docker logs -f
- docker commit
- docker build -t imag:tag .
- docker tag image_id newImage:tag

## Dockerfile

- ENTRYPOINT run指令不覆盖
- CMD run指令覆盖
