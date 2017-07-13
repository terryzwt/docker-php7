###简介
* 此镜像包含基于php7运行Drupal所需的基本扩展，可以在生产环境使用。

###文件介绍
* 所有镜像，都已经包含drush 和 composer 命令。drush版本8.1.2
* /app/web为网站文件的挂在目录。


|目录|简介|
| ----- | ----- |
|7.1/base/Dockerfile|php 7.1的Drupal运行环境的基础镜像，包含gd,pdo_mysql等扩展|
|7.1/memcached/Dockerfile|基于base镜像+php memcached扩展|
|7.1/redis/Dockerfile|包基于base镜像+php redis扩展|
|7.1/oci8/Dockerfile|包基于base镜像+php oci8扩展|
|7.1/package/Dockerfile|包基于base镜像+php redis,memcached,oci8扩展|


###备注
* 详细工作方式，请见[这里](https://github.com/terryzwt/compose-lnmp-drupal)
* 如果已经有lnmp或lamp环境，只是想体验下php7，推荐如下方式执行(假设宿主机代码放在/app/web)：

```bash
docker run -d --name php7-fpm -p:9007:9000 -v /app/web:/app/web zterry95/docker-php7:7.1-memcached
```
如上命令将开启9007端口作为fpm的端口，修改nginx或者apache的配置，将端口号指向9007，重启nginx或apache即可。

需要注意的是，如果代码不是放置在/app/web目录，nginx或fpm的配置需要相应变更。
test
