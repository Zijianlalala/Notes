# Mysql修改表中字段编码

## 修改表的编码方式
`ALTER TABLE `test` DEFAULT CHARACTER SET utf8;`

## 修改字段的编码方式
`ALTER TABLE `test` CHANGE `name` `name` VARCHAR(36) CHARACTER SET utf8 NOT NULL`
