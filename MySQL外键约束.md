# MySQL外键约束
#编程/MySQL
## 常用外键约束
1. 父表更新时子表也更新 父表删除时 若子表有匹配项 则删除失败
`ON UPDATE CASCADE ON DELETE RESTRICT`
2. 父表更新时子表也更新 父表删除时 子表的匹配项也删除
`ON UPDATE CASCADE ON DELETE CASCADE`
