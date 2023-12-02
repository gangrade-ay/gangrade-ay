- 👋 Hi, I’m @gangrade-ay
- 👀 I’m interested in ...
- 🌱 I’m currently learning docker.
- Docker Low memory optimization of MySQL for 256MB system.
- docker run -d --net=host --name mysql -e MYSQL_ROOT_PASSWORD=password --memory=256m --memory-swap=0m mysql:latest --performance_schema=off --innodb_buffer_pool_size=5m --max_connections=5 --sort_buffer_size=2m --key_buffer_size=8m --innodb_log_buffer_size=256K --innodb_sort_buffer_size=64K --thread_cache_size=0 --host_cache_size=0 --thread_stack=128k --tmp_table_size=16M
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
gangrade-ay/gangrade-ay is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

Nextcloud Docker Server config (Basic) with mysql backend running with memory optimization for low memory usage requirement:
docker network create nextcloud_network

docker run -d \
  --cpus="1" \
  --memory=1GB \
  --memory-swap=1GB \
  --name nextcloud \
  --network nextcloud_network \
  -p 8080:80 \
  nextcloud

docker run -d --name mysql_nextcloud --network nextcloud_network -p 3306:3306 -e MYSQL_ROOT_PASSWORD=ROOT_Password -e MYSQL_DATABASE=nextcloud -e MYSQL_USER=nextcloud_user -e MYSQL_PASSWORD=PASSWORD --cpus=1 --memory=512MB --memory-swap=512MB mysql:latest --performance_schema=off --innodb_buffer_pool_size=5m --max_connections=5 --sort_buffer_size=2m --key_buffer_size=8m --innodb_log_buffer_size=256K --innodb_sort_buffer_size=64K --thread_cache_size=0 --host_cache_size=0 --thread_stack=128k --tmp_table_size=16M

/// Attention - Change mysql root and user password before starting docker
