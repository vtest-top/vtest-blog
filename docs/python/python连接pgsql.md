## 安装 psycopg 库

```sh
pip install psycopg
```

## Python psycopg2 模块 `APIs`

| 序号 | API                                                                                                         | 描述                                                                                                                                                                                  |
| ---- | ----------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1    | `psycopg2.connect(database="testdb", user="postgres", password="cohondob", host="127.0.0.1", port="5432") ` | 这个 API 打开一个连接到 PostgreSQL 数据库。如果成功打开数据库时，它返回一个连接对象。                                                                                                 |
| 2    | `connection.cursor()`                                                                                       | 该程序创建一个光标将用于整个数据库使用 Python 编程                                                                                                                                    |
| 3    | ` cursor.execute(sql [, optional parameters])`                                                              | 此例程执行 SQL 语句。可被参数化的 SQL 语句（即占位符，而不是 SQL 文字）。 psycopg2 的模块支持占位符用％s 标志。例如：cursor.execute("insert into people values (%s, %s)", (who, age)) |
| 4    | `curosr.executemany(sql, seq_of_parameters)`                                                                | 该程序执行 SQL 命令对所有参数序列或序列中的 sql 映射。                                                                                                                                |
| 5    | `curosr.callproc(procname[, parameters])`                                                                   | 这个程序执行的存储数据库程序给定的名称。该程序预计为每一个参数，参数的顺序必须包含一个条目。                                                                                          |
| 6    | `cursor.rowcount`                                                                                           | 这个只读属性，它返回数据库中的行的总数已修改，插入或删除最后 execute\*().                                                                                                             |
| 7    | `connection.commit()`                                                                                       | 此方法提交当前事务。如果不调用这个方法，无论做了什么修改，自从上次调用 commit()是不可见的，从其他的数据库连接。                                                                       |
| 8    | `connection.rollback()`                                                                                     | 此方法会回滚任何更改数据库自上次调用 commit（）方法。                                                                                                                                 |
| 9    | `connection.close()`                                                                                        | 此方法关闭数据库连接。请注意，这并不自动调用 commit（）。如果你只是关闭数据库连接而不调用 commit（）方法首先，那么所有更改将会丢失！                                                  |
| 10   | `cursor.fetchone()`                                                                                         | 这种方法提取的查询结果集的下一行，返回一个序列，或者无当没有更多的数据是可用的。                                                                                                      |
| 11   | `cursor.fetchmany([size=cursor.arraysize])`                                                                 | 这个例程中取出下一个组的查询结果的行数，返回一个列表。当没有找到记录，返回空列表。该方法试图获取尽可能多的行所显示的大小参数。                                                        |
| 12   | `cursor.fetchall()`                                                                                         | 这个例程获取所有查询结果（剩余）行，返回一个列表。空行时则返回空列表。                                                                                                                |

## 操作 PGSQL

```python
import psycopg2

host = '10.59.79.79'
port = '5433'
db_name = 'test_db_name'
# db_models = 'public'
username = 'postgres'
password = 'postgres'

conn = psycopg2.connect(
    host=host,
    port=port,
    user=username,
    password=password,
    database=db_name,
)

cur = conn.cursor()
insql = 'select * from t_test'
cur.execute(insql)
conn.commit()
conn.close()

```
