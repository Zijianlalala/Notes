# Android学习笔记
## Intent
定义：是一个消息传递对象

分类：

- 显示intent：用于指定要启动的Activity
- 隐式intent：用于其他应用提供的功能

--

### 新建一个Intent
`Intent intent = new Intent(Context context,Object objetc);`

### 在按钮监听事件里调用另一个Activity
`startActivity(intent);`

### 利用Intent传递参数(键值对的形式)

```
Intent putExtra(String name,String value)//传递信息
getStringExtra(String name)//获取信息
hasExtra()//判断该Intent是否有data
```
在`startActivity(intent)`之前先确保设备上的某些应用可以处理该Intent

```
if(intent.resolveActivity(getPackageManager())!= null) {
	startActivity(intent);
}
```
### 在配置文件中向NewAcitivity添加向下按钮
```
<activity android:name=".NewActivity"
            android:parentActivityName=".MainActivity">
            <meta-data
                android:name="android.support.PARENT_ACTIVITY"
                android:value=".MainActivity"/>
</activity>
```
### 常用的Intent
- String传递参数

```
//第一个Activity中的点击事件的方法中
Intent intent = new Intent(MainActivity.this,newActivity.class);
intent.putExtra("key",value);
startActivity(intent);
//在调用的Activity中的onCreate()方法中
Intent intent = getIntent();
if (!intent) {
	if(intent.hasExtra("key")) {
	value = intent.getStringExtra("key");
	mTextView.setText(value);
	}
}
```
- 地图
- 分享型Intent

```
//创建分享型Intent对象
private Intent createShareForecastIntent() {
        Intent shareIntent = ShareCompat.IntentBuilder.from(this)
                .setType("text/plain")
                .setText(mForecast + FORECAST_SHARE_HASHTAG)
                .getIntent();
        return shareIntent;
    }
```