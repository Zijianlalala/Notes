# Android学习笔记九
-
### 弹出对话框
```
 new AlertDialog.Builder(getActivity)
 	.setTitle("TITLE")
 	.setResult(Activtiy.RESULT_OK, null)
 	.create()
 	.show();
```

### 设置工具栏
1. 在res/menu/中新建menu文件
2. 在fragment中重写` onCreateOptionsMenu()方法`将新建的Menu文件填充到menu实例中

```
@override
public void onCreateOptionsMenu(Menu menu, MenuInflater inflater) {
	super.onCreateOptionsMenu(menu, inflater);
	inflater.inflate(R.menu.new_menu, menu);
}
```
3.重写`onCreate()`方法

```
@override
public void onCreate(Bundle saveInstanceState) {
	super.onCreate(saveInstanceState);
	//让FragmentManager知道Fragment需接收选项菜单方法回调
	setHasOptionsMenu(true);
	
}

```
### 实现工具类内按钮的操作
在Fragment中重写`onOptionItemSelected(MenuItem item)`

```
@override 
public boolean onOptionItemSelected(Menu  item) {
	switch (item.getItemId()) {
		case R.id.menu_new_item:
			//operations what you want to do
			return true;
		default:
			return super.onOptionItemSelected(item);
	}
}
```

### 后退键
1. 临时性导航：只能返回到上一次浏览过的用户界面
2. 层级式导航：应用内逐级向上导航

```
//实现层级式导航只需要在有menu的基础上更改Manifests文件
//manifestes.xml
<activity
		android:name=".BxxzActivity"
		android:parentActivtiyName=".AxxxActivty"/>
```