# Android学习笔记六
### 实现Button的监听器

```
mButton.setOnClickListener(new View.onClickListener {
	@override
	public void onClick(View v) {
	//things you want to do 
	}
});
```

### 设置一个Toast

```
//第一个参数是该Activity的一个实例，
//第二个参数是字符串的id
//第三个参数是显示时间
Toast.makeText(Context context,int resId, int duration).show() 
```

### onSaveInstanceState(Bundle outState)
刚方法默认实现要求所有activity视图将自身状态数据保存在Bundle对象中。
### Bundle
定义：存储字符串键与限定类型值之间映射关系（键值对）的一种结构
