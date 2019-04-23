### Hive执行方式
- CLI方式，开启hive客户端
- 字符串执行，通过`hive -e STRING调用`
- 文件执行，通过`hive -f FILE.sql`



#### 字符串执行
- 简单的查询命令可以直接写命令，可以直接通过“>”将结果导出到文件：`hive -e "select * from TABLE_NAME" > FILE`
- 编写.sh文件，可以直接执行shell文件来执行hive
```shell
sql=$(cat <<!EOF

use bigdata_jy;
select * from orders limit 10;

!EOF)

echo $sql
cd $HIVE_HOME
hive -e "$sql"

exitCode=$?
if [ $exitCode -ne 0 ]:then
        echo "hive execute failed
        exit $exitCode
fi

```


### 文件执行
编写文件text.sql，比如文件内容如下所示：

```sql
use bigdata_jy;
select * from orders limit 10;
```
在命令行下执行：`hive -f text.sql`

