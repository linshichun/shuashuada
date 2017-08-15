# 安装nginx
## 安装
```
rm -rf nginx-1.4.4

wget http://oss.aliyuncs.com/aliyunecs/onekey/nginx/nginx-1.4.4.tar.gz

tar zxvf nginx-1.4.4.tar.gz
cd nginx-1.4.4
./configure --user=www \
--group=www \
--prefix=/webdata/server/nginx \
--with-http_stub_status_module \
--without-http-cache \
--with-http_ssl_module \
--with-http_gzip_static_module \
--with-pcre=../pcre-8.12 \
--with-pcre-jit \
--add-module=../ngx_cache_purge-2.3

make

make install
chmod 775 /webdata/server/nginx/logs
chown -R www:www /webdata/server/nginx/logs
chmod -R 775 /webdata/www
chown -R www:www /webdata/www
cd ..
cp -fR ./nginx/config-nginx/* /webdata/server/nginx/conf/
sed -i 's/worker_processes  2/worker_processes  2/' /webdata/server/nginx/conf/nginx.conf
chmod 755 /webdata/server/nginx/sbin/nginx
#/webdata/server/nginx/sbin/nginx
mv /webdata/server/nginx/conf/nginx /etc/init.d/
chmod +x /etc/init.d/nginx
/etc/init.d/nginx start
```
## 修改端口号
http://www.4u4v.net/structures-lnamp-linux-apache-nginx-mysql-php-front-end-web-php-development-environment.html

http://javapyer.iteye.com/blog/1986092

## Nginx添加proxy_cache模块
wget http://labs.frickle.com/files/ngx_cache_purge-2.3.tar.gz

./configure \
--user=www \
--group=www \
--prefix=/usr/local/nginx \
--add-module=../nginx_mod_h264_streaming-2.2.7 \
--with-http_flv_module \
--with-http_stub_status_module \
--with-http_ssl_module \
--with-http_mp4_module \
--with-http_gzip_static_module --with-pcre=../pcre-8.32 --with-pcre-jit --add-module=../ngx_cache_purge-2.0


# 安装nginx1.8
http://www.cnblogs.com/kevingrace/p/5882006.html

 yum install -y pcre pcre-devel openssl openssl-devel gcc
 wget http://nginx.org/download/nginx-1.8.0.tar.gz
  tar -zxvf nginx-1.8.0.tar.gz
   cd nginx-1.8.0
   
./configure --prefix=/webdata/server/nginx \
--user=www \
--group=www \
--with-http_ssl_module \
--with-http_flv_module \
--with-http_stub_status_module \
--with-http_gzip_static_module \
--with-pcre

[root@node1 src]# make && make install


# php 5.5.7

## 创建安装目录
```
mkdir -p /webdata/server/php-5.5
```
## 下载包
wget http://oss.aliyuncs.com/aliyunecs/onekey/php/php-5.5.7.tar.gz

## 解压
tar zxvf php-5.5.7.tar.gz

## 切换到解压目录
cd php-5.5.7

## 编译
```
./configure --prefix=/webdata/server/php-5.5 \
--enable-opcache \
--with-config-file-path=/webdata/server/php-5.5/etc \
--with-mysql=mysqlnd \
--with-mysqli=mysqlnd \
--with-pdo-mysql=mysqlnd \
--enable-fpm \
--enable-fastcgi \
--enable-static \
--enable-inline-optimization \
--enable-sockets \
--enable-wddx \
--enable-zip \
--enable-calendar \
--enable-bcmath \
--enable-soap \
--with-zlib \
--with-iconv=/usr/local \
--with-gd \
--with-xmlrpc \
--enable-mbstring \
--without-sqlite \
--with-curl \
--enable-ftp \
--with-mcrypt  \
--with-freetype-dir=/usr/local/freetype.2.1.10 \
--with-jpeg-dir=/usr/local/jpeg.6 \
--with-png-dir=/usr/local/libpng.1.2.50 \
--disable-ipv6 \
--disable-debug \
--with-openssl \
--disable-maintainer-zts \
--disable-safe-mode \
--disable-fileinfo
```

```
make ZEND_EXTRA_LIBS='-liconv' -j
```

```
make install
```

## 配置php.ini
```
cd ..
cp ./php-5.5.7/php.ini-production /webdata/server/php-5.5/etc/php.ini
```
```
sed -i 's#; extension_dir = \"\.\/\"#extension_dir = "/webdata/server/php-5.5/lib/php/extensions/no-debug-non-zts-20121212/"#'  /webdata/server/php-5.5/etc/php.ini
sed -i 's/post_max_size = 8M/post_max_size = 64M/g' /webdata/server/php-5.5/etc/php.ini
sed -i 's/upload_max_filesize = 2M/upload_max_filesize = 64M/g' /webdata/server/php-5.5/etc/php.ini
sed -i 's/;date.timezone =/date.timezone = PRC/g' /webdata/server/php-5.5/etc/php.ini
sed -i 's/;cgi.fix_pathinfo=1/cgi.fix_pathinfo=1/g' /webdata/server/php-5.5/etc/php.ini
sed -i 's/max_execution_time = 30/max_execution_time = 300/g' /webdata/server/php-5.5/etc/php.ini
```
##配置端php-fpm
```
cp /webdata/server/php-5.5/etc/php-fpm.conf.default /webdata/server/php-5.5/etc/php-fpm.conf
sed -i 's,user = nobody,user=www,g'   /webdata/server/php-5.5/etc/php-fpm.conf
sed -i 's,group = nobody,group=www,g'   /webdata/server/php-5.5/etc/php-fpm.conf
sed -i 's,^pm.min_spare_servers = 1,pm.min_spare_servers = 5,g'   /webdata/server/php-5.5/etc/php-fpm.conf
sed -i 's,^pm.max_spare_servers = 3,pm.max_spare_servers = 35,g'   /webdata/server/php-5.5/etc/php-fpm.conf
sed -i 's,^pm.max_children = 5,pm.max_children = 100,g'   /webdata/server/php-5.5/etc/php-fpm.conf
sed -i 's,^pm.start_servers = 2,pm.start_servers = 20,g'   /webdata/server/php-5.5/etc/php-fpm.conf
sed -i 's,;pid = run/php-fpm.pid,pid = run/php-fpm.pid,g'   /webdata/server/php-5.5/etc/php-fpm.conf
sed -i 's,;error_log = log/php-fpm.log,error_log = /webdata/log/php-5.5/php-fpm.log,g'   /webdata/server/php-5.5/etc/php-fpm.conf
sed -i 's,;slowlog = log/$pool.log.slow,slowlog = /webdata/log/php-5.5/\$pool.log.slow,g'   /webdata/server/php-5.5/etc/php-fpm.conf
```


## 修改端口号
vi /webdata/server/php-5.5/etc/php-fpm.conf
```
; Note: This value is mandatory.  
listen = 127.0.0.1:9005
```

##
```
install -v -m755 ./php-5.5.7/sapi/fpm/init.d.php-fpm  /etc/init.d/php-fpm5.5
/etc/init.d/php-fpm5.5 start
```
