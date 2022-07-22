```shell
## 拉取docker镜像
docker pull redis:latest
# 使用带密码的命令启动redis
docker run --name redis -p 6379:6379 -d --restart=always redis redis-server --appendonly yes --requirepass "Redis110120.."

docker run --name redis -p 6379:6379 -d --restart=always redis redis-server --appendonly yes --requirepass "RedisRedis110120.."
```





01-com.alibaba.ae.payment.cashier.product.apm.paymentchannel.wrapper.DefaultCashierChannelWrapper#checkSupportAliPay
