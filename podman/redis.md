docker run -d --restart=always --name redis \
-p 6379:6379 \
redis redis-server \
--appendonly yes \
--requirepass "redis_password"