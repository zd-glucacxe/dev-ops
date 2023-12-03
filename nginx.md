// 将 Nginx 容器中的 nginx.conf 文件复制到本地的 D:\MyProject\chatgpt\dev-ops\nginx\conf 目录中
docker container cp Nginx:/etc/nginx/nginx.conf D:\MyProject\chatgpt\dev-ops\nginx\conf

//将 Nginx 容器中的 default.conf 文件复制到本地目录 D:\MyProject\chatgpt\dev-ops\nginx\conf\conf.d，并命名为 default.conf。
docker container cp Nginx:/etc/nginx/conf.d/default.conf D:\MyProject\chatgpt\dev-ops\nginx\conf\conf.d\default.conf

// 用于将 Nginx 容器中的 index.html 文件复制到本地目录 D:\MyProject\chatgpt\dev-ops\nginx\html。
docker container cp Nginx:/usr/share/nginx/html/index.html D:\MyProject\chatgpt\dev-ops\nginx\html

//在Docker容器中运行Nginx，并通过挂载卷（volumes）来配置Nginx的日志、HTML文件和其他相关文件
docker run --name Nginx -p 80:80 -v D:/MyProject/chatgpt/dev-ops/nginx/logs:/var/log/nginx -v D:/MyProject/chatgpt/dev-ops/nginx/html:/usr/share/nginx/html -v D:/MyProject/chatgpt/dev-ops/nginx/conf/nginx.conf:/etc/nginx/nginx.conf -v D:/MyProject/chatgpt/dev-ops/nginx/conf/conf.d:/etc/nginx/conf.d -v D:/MyProject/chatgpt/dev-ops/nginx/ssl:/etc/nginx/ssl/ --privileged=true -d --restart=always nginx

1. 对于Nginx容器，尝试访问 http://localhost/ 或 http://127.0.0.1/，因为你将容器的80端口映射到主机的80端口上。
2. 对于Portainer容器，尝试访问 http://localhost:9000/ 或 http://127.0.0.1:9000/，因为你将容器的9000端口映射到主机的9000端口上。