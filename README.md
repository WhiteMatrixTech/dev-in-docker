# 常用 Docker 镜像

包括 Redis、 MongoDB、 MySQL 等。

进入对应目录后，执行

```bash
# 启动
docker-compose up -d
# 停止
docker-compose down
```

## 安全说明

这些配置只用于本地开发：服务没有开启认证或使用弱口令（例如 Redis、MongoDB 没有密码，MySQL 的 root 密码是 `123456`）。
因此所有端口默认只绑定到 `127.0.0.1`，只有本机可以访问。

如果确实需要让其他机器访问，请先修改默认密码、开启认证，再把对应 `docker-compose.yml` 里 `ports` 的 `127.0.0.1` 改成需要监听的地址，例如：

```yaml
ports:
  - "0.0.0.0:6379:6379"
```

注意：Docker 发布的端口不受 `ufw` 等主机防火墙规则限制。
