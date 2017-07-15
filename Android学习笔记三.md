# Android学习笔记三
---
####关键字：json、Menu
---
### 在android中获取json数据
举例：

```
{
	"name":{
		"firstName":"John",
		"lastName":"Doe"
	}
	"title":"Missing Person"
}
```

1. 初始化json对象 
` JSONObject contact = new JSONObject(JSONString);`

2. 再声明一个name对象
` JSONObject name = contact.getJSONObject("name");`
3. 获取key值对应的信息

```
String firstName = name.getString("firstName");
String lastName = name.getString("lastName");		
```

### 创建Menu
- 创建RES/menu/menuName.xml并设置id和title
- 在MainActivity中重写onCreateOptionsMenu

```
@Override
public boolean onCreateOptionsMenu(Menu menu) {
	MenuInflater inflater = getMenuInflater();
	inflater.inflate(R.menu.menuName, menu);
	return true;
}
```
- 重写onOptionsItemSelected

```
@Override
    public boolean onOptionsItemSelected(MenuItem item) {
        int id = item.getItemId();
        if (id == R.id.action_refresh) {
            //省略具体的操作
            return true;
        }
        return super.onOptionsItemSelected(item);
    }
```