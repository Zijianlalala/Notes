# Android学习笔记四
---
#### 关键词：dp/sp
---
### dp/sp
- px = dp*(dpi/160) （dpi：Dots per inch）
- 文字的尺寸一般用sp 

### Android的四种数据存储方式
1. SharedPreferences
2. SQLite
3. Content Provider
4. File

### SharedPreferences
1. 一种轻微的数据存储方式
2. 本质是基于XML文件存储key-value键值对数值
3. 通常用来存储一下简单的配置信息