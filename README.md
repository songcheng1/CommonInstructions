Docker常用指令：

```python
		开启docker： systemctl start docker

		重启docker： systemctl restart docker

		关闭docker： systemctl stop docker

	# 镜像操作：
	
		查询镜像列表： docker images

		删除镜像： docker rmi 镜像id

	# 容器操作：
	
		启动容器：docker start 容器id

		重启容器：docker restart 容器id

		停止容器：docker stop 容器id

		删除容器：docker rm 容器id

	1.一条命令实现停用并删除容器：

		docker stop $(docker ps -q) & docker rm $(docker ps -aq)

		docker rm $(docker container ls -f "status=exited" -q)

	2.删除所有容器

		docker rm $(docker ps -aq)

	3.停用全部运行中的容器

		docker stop $(docker ps -q)

	4.进入容器

		docker exec -it 容器id(eg:d27bd3008ad9 ) /bin/bash

	5.查看容器ip

		docker inspect 36afde543eb5 | grep IPAddress

	6.docker-compose

		docker-compose up

		docker-compose up -d

		docker-compose -f docker-compose-aliyun.yml build --no-cache image

		docker-compose -f docker-compose-aliyun.yml up -d test(prod)

	7.docker日志查询

		docker logs -f -t --since=日期 --tail=条数  容器id

		例如：docker logs -f -t --since="0000-00-00" --tail=100  6000bfea0ece

	8.将docker容器中的文件拉到本地

		docker cp  容器id:容器内日志路径 .（点切勿忘记）
		
		例如：docker cp  67aef1c194ef:/app/yml_img .

```

绿色独角兽发布启动指令：

	nohup gunicorn -w 并发数 -b IP:端口号 脚本名称:应用app名称 & # 后台执行

	例如： nohup gunicorn -w 4 -b 0.0.0.0:5000 manage:app &


linux 提取进程id以及结束该名称下的所有进程：

	# 提取进程id  （运行文件为：main.py）

	ps -aux|grep main.py| grep -v grep | awk '{print $2}'

	# 结束main.py所有进程

	ps -aux|grep main.py| grep -v grep | awk '{print $2}' | xargs kill -9


