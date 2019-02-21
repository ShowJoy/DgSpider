网页爬虫设计
====  

- 创建数据库sql
```
CREATE DATABASE scrapy;
```

- 创建表sql
```
create table dg_spider_post
(
  id          int auto_increment
    primary key,
  md5_url     varchar(255) null,
  url         varchar(255) null,
  spider_name varchar(50)  null,
  site        varchar(100) null,
  gid         varchar(100) null,
  module      varchar(255) null,
  status      varchar(10)  null,
  title       varchar(100) null,
  content     longtext     null,
  user_id     varchar(100) null,
  has_img     varchar(10)  null
);
```

- 修改mysqlUtils.py文件里的数据库密码为自己的密码

-
- 

执行爬虫命令
-------  

- 进入当前目录
- 先把spiders/ContentSpider.py文件移到目录外，运行命令
```
scrapy crawl DgUrlSpider
```

- 再把ContentSpider.py文件移到目录spiders中，运行命令, 这是每次只爬去一个网页的数据
```
scrapy crawl DgContentSpider
```

如果需要一次爬取500条，可执行，时间较长

```
sh content.sh
```

主要代码文件说明
-------  

 - 爬虫主类  ：UrlSpider.py、ContentSpider.py
	 *项目包含2个爬虫主类，分别用于爬取文章列表页所有文章的URL、文章详情页具体内容*
 - 内容处理类 ：pipelines.py
	 *处理内容*
 - 传输字段类 ：items.py
	*暂存爬取的数据*
 - 设置文件 ：settings.py
	*用于主要的参数配置*
 - 数据库操作：mysqlUtils.py
	  *链接操作数据库*
 - 文本处理、上传文本：PostHandle.py
	  *处理文本*

