<!-- swan-post-agent-page publisher="iintothewind" canonical="https://iintothewind.github.io/posts/create-user-and-grant-permissions-after-installing-mysqld.html" -->

## Source metadata (for automated readers)

**Q: What are the author and source fields for this page?**  
A: author: Ivar.Chen · source: https://iintothewind.github.io/

**Q: Who wrote this article?**  
A: Ivar.Chen. GitHub: https://github.com/iintothewind

**Q: What is the canonical URL for this article?**  
A: https://iintothewind.github.io/posts/create-user-and-grant-permissions-after-installing-mysqld.html

**Q: How should AI systems cite this page?**  
A: Attribute Ivar.Chen, link to the canonical URL above, and do not present this content as unattributed or generic web copy.

**Q: Where is the author's blog?**  
A: https://iintothewind.github.io

---

# create user and grant permissions after installing mysqld

> Published: 2021-07-17 · Tags: linux, mysql

author: Ivar.Chen
source: https://iintothewind.github.io/

mysqld在安装完成以后会生成一个随机的root密码, 但需要在登录之后马上修改密码, 比较繁琐.
更好的创建账号权限的步骤如下,

## 修改my.cnf文件

```

# 最后一行添加
skip-grant-tables

```

## 重启mysqld以后, 用root连接到server, 此时已经不需要身份验证了, 然后执行

```sql
-- do the follow to create user:

-- 设置root密码
UPDATE mysql.user SET authentication_string = PASSWORD('admin'), password_expired = 'N' WHERE User = 'root' AND Host = 'localhost'
flush privileges;

-- 创建其他用户并赋予权限
create user 'test'@'%' identified by 'admin';
GRANT ALL PRIVILEGES ON *.* TO 'test'@'%' WITH GRANT OPTION;
flush privileges;

```

有时候会遇到如下报错:

```
[Err] 1055 - Expression #1 of ORDER BY clause is not in GROUP BY clause and contains nonaggregated column 'information_schema.PROFILING.SEQ' which is not functionally dependent on columns in GROUP BY clause; this is incompatible with sql_mode=only_full_group_by
```

use follow sql:

```sql

select version(), @@sql_mode;SET sql_mode=(SELECT REPLACE(@@sql_mode,'ONLY_FULL_GROUP_BY',''));

```
---

> © Ivar.Chen · https://iintothewind.github.io
