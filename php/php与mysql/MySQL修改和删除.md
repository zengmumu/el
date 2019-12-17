# MySQL Update Set 更新数据

## UPDATE 更新

UPDATE SET 语法用于修改更新数据表中的数据。

语法：

    
    
    UPDATE tb_name SET column1 = new_value1,column2 = new_value2,… WHERE definition
    

该语法将数据表中符合 WHERE 条件的记录中的 column1 的值更新为 new_value1，column2 的值更新为 new_value2
，以此类推。如果省略 WHERE 条件，则会将表中所有记录的 column 值进行更新。

例子：

    
    
   
    
   UPDATE user SET email = 'xiaoming@163.com' WHERE username = '小明';
   
    

更新前数据： uid | username | password | email | regdate  
---|---|---|---|---  
1 | admin | b7e591c246d010bb2ccd77d52490c85e | admin@5idev.com | 1277992339  
2 | 小明 | a193686a53e4de85ee3f2ff0576adf01 | xiao@163.com | 1278063917  
3 | Jack | 0193686a35e4de85ee3f2ff0567adf49 | jack@gmail.com | 1278061380  
4 | 小王 | e10adc3949ba59abbe56e057f20f883e | 12345@163.com | 1289632955  
  
例子将 user 表中 username 为 小明 的 email 修改为 xiaoming@163.com 。

更新后数据： uid | username | password | email | regdate  
---|---|---|---|---  
1 | admin | b7e591c246d010bb2ccd77d52490c85e | admin@5idev.com | 1277992339  
2 | 小明 | a193686a53e4de85ee3f2ff0576adf01 | xiaoming@163.com | 1278063917  
3 | Jack | 0193686a35e4de85ee3f2ff0567adf49 | jack@gmail.com | 1278061380  
4 | 小王 | e10adc3949ba59abbe56e057f20f883e | 12345@163.com | 1289632955  
  
## UPDATE 表达式

UPDATE 语法允许 SET 后面跟表达式。

例子 1 ：

    
    
    UPDATE article SET pv = pv+1 WHERE id = 123
    

该例子让 id 为 123 的文章在被点击阅读的时候点击量加 1 。

## DELETE 删除

DELETE FROM 语法用于删除数据表的数据记录。

语法：
    
    
    DELETE FROM tb_name WHERE definition
    

该语法将数据表中符合 WHERE 条件的数据记录删除。如果省略WHERE条件，则会将表中记录全部删除。

例子：
    
    
   DELETE FROM user WHERE username = '小王';
   
    

删除数据成功，浏览器输出：

    
    
    删除 1 条数据记录。
    

删除前数据： uid | username | password | email | regdate  
---|---|---|---|---  
1 | admin | b7e591c246d010bb2ccd77d52490c85e | admin@5idev.com | 1277992339  
2 | 小明 | a193686a53e4de85ee3f2ff0576adf01 | xiao@163.com | 1278063917  
3 | Jack | 0193686a35e4de85ee3f2ff0567adf49 | jack@gmail.com | 1278061380  
4 | 小王 | 0193686a35e4de85ee3f2ff0567adf49 | 12345@163.com | 1278061380  

删除后数据： uid | username | password | email | regdate  
---|---|---|---|---  
1 | admin | b7e591c246d010bb2ccd77d52490c85e | admin@5idev.com | 1277992339  
2 | 小明 | a193686a53e4de85ee3f2ff0576adf01 | xiaoming@163.com | 1278063917  
3 | Jack | 0193686a35e4de85ee3f2ff0567adf49 | jack@gmail.com | 1278061380  
  


