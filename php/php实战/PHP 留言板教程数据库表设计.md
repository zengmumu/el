# PHP 留言板教程数据库表设计

## 留言板数据库表设计

根据前文留言板功能需求分析， 对应的 guestbook 表结构如下：

字段名 | 数据类型 | NULL 属性 | 说明  
---|---|---|---  
id | mediumint | NOT NULL | 主键，自动增长  
nickname | char(16) | NOT NULL | 留言者称呼  
email | varchar(60) | NULL | 留言者 Email  
content | text | NOT NULL | 留言内容  
createtime | int | NOT NULL | 留言时间戳  

  
建表 SQL 参考如下：

    
    
    CREATE TABLE `guestbook` (
      `id` mediumint(8) unsigned NOT NULL auto_increment,
      `nickname` char(16) NOT NULL default '',
      `email` varchar(60) default NULL,
      `content` text NOT NULL,
      `createtime` int(10) unsigned NOT NULL default '0',
      PRIMARY KEY  (`id`)
    ) ENGINE=MyISAM  DEFAULT CHARSET=utf8 AUTO_INCREMENT=1;
    


    

