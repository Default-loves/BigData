
### 数据格式
```
1,user1,book-music-tv,guangdong:guangzhou-anhui:bozhou
2,user2,game-code,guangxi:guilin-beijing-beijing
3,user3,book-basketball,hunan:wuhan
```

### Hive建表和插入数据
```
create table create_array_map(
   id int,
   name string,
   hobby array<string>,
   address map<string, string>
)
row format delimited
fields terminated by ','
collection items terminated by '-'
map keys terminated by '|'
stored as textfile;

load data local inpath './data/create_array_map.txt' overwrite into table create_array_map;
```

### 查看数据
![image](https://github.com/Default-loves/BigData/blob/master/pic/hive_create_table_array_map.png?raw=true)
