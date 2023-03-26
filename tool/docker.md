#

## 命令

- docker run
  - -it 交互式
  - -d 后台运行
  - -p | -P 随机端口
  - --name
  - type=volume,src=todo-db,target=/etc/todos # 挂载数据卷
  - type=bind,src=/home/xxx,target=/etc/todos # 挂载宿主机目录
- docker ps
- docker stop | docker rm -f container_id
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

## docker-compose

- docker-compose up -d

## best practice

- [language-overview](https://docs.docker.com/language/)
- [nodejs](https://nodejs.org/en/docs/guides/nodejs-docker-webapp/)

## apps

```bash
# mysql
docker run -d --network network -e MYSQL_ROOT_PASSWORD=root --name mysql -v mysqlData:/var/lib/mysql -p 3306:3306 mysql

```
