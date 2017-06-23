Moell Blog 安装文档

获取源码

源码地址：Github

git clone https://github.com/moell-peng/moell-blog.git
环境要求

参照Laravel文档：Laravel5.2 Document
PHP : 5.6+
MYSQL : 5.6+

安装Composer

curl -sS https://getcomposer.org/installer | php
进入项目目录

cd moell-blog
安装项目依赖

composer install
生成.env

cp .env.example .env
php artisan key:generate
配置数据库信息

创建数据库，将数据库信息填写至.env(必须先创建数据库,登录mysql,创建homestead用户和homestead database,否则后面会出错)


运行数据迁移和数据填充

php artisan migrate
php artisan db:seed
将项目根目录指向入口public目录

Nginx

location / {
        root   /www/moell-blog/public;
        try_files $uri $uri/ /index.php?$query_string;
        index  index.php index.html index.htm;
}
设置目录权限

chown -R nginx:nginx  storage/
chmod -R 755 public/
chown -R nginx:nginx  public/
调优

php artisan optimize
php artisan config:cache
php artisan route:cache
后台登录

后台地址: 域名/backend
email：moell@foxmail.com
password : moell.cn

最后

如果本项目对你有帮助，欢迎 star 本项目。
