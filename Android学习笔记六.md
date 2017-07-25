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
### Activity的生命周期
旋转屏幕后会对Activity进行销毁并重新调用onCreate方法
所以要对Activity的当前状态进行保存处理故用到onSavaInstanceState()方法
### onSaveInstanceState(Bundle outState)
刚方法默认实现要求所有activity视图将自身状态数据保存在Bundle对象中。
### Bundle
定义：存储字符串键与限定类型值之间映射关系（键值对）的一种结构
### 调用有返回值的子Activity
`public void startActivityForResult(Intent intent, int requestCode)`
第二个参数是请求代码，用于判断区分多个子Activity的消息回馈方
### 设置返回结果
有两种方法实现子Activity发送返回结果给父Activity

1. `public final void setResult(int resultCode)`
2. `public final void setResult(int resultCode, Intent data)`

一般来说ResultCode是一下两个自定义常量中的任意一个

- Activity.RESULT_OK
- Activity.RESULT_CANCLE
 
### 在父Activity中获取子Activity的返回结果

重写`protected void onActivityResult(int requestCode, int resultCode, Intent data)` 方法

该方法第一个参数来自父Activity中原始请求代码，二、三参数来自子Activity的setResult()参数





