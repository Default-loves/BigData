主要用于行转列，一行有多个数据聚合而成，对聚合数据进行拆分

### 源数据
```
//123.txt
user1 12-13-14-15
user2  16-17-18
user3 1-2-3-4-5-6-7
```

### 建表
```
create table text_lateral_view(
   game_id string,
   user_ids string
)
row format delimited
fields terminated by '\t'
stored as textfile;
```
### 加载数据
`load data local inpath './123.txt' overwrite into table text_lateral_view;`
![image](https://github.com/Default-loves/BigData/blob/master/pic/QQ%E6%88%AA%E5%9B%BE20190419103542.png?raw=true)

### 行转列
```
select game_id, user_id
from text_lateral_view
lateral view explode(split(user_ids,'\\-')) abc as user_id;
```
![image](https://github.com/Default-loves/BigData/blob/master/pic/QQ%E6%88%AA%E5%9B%BE20190419103556.png?raw=true)
