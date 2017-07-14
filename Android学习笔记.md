#Andorid学习笔记一
-
###Android四大组件
1. Activity
2. Service
3. Content Provider
4. Broadcast Recevier

-
###四大组件之Activity
####定义
是用户可以执行的单一任务
####作用
负责创建新的窗口供应绘制和从系统中接受事件

####实现
读取res/layout中的xml布局文件确定创建哪些视图

####视图类型
1. UI组件 例如：TextView,EditText,Button等
2. 容器视图 例如：线性布局，相对布局等

####XML属性
1. Text 

```
android:text="This is a Text"
```
2. 宽度和高度


```
android:layout_width="200dp"
android:layout_height="300dp"
```
一般自适应为wrap_content和match_content
3. Padding和Margin
区别是padding是确定视图里面的边界，而layout_margin确定的是视图外的边界

####XML与Java Activitu关联
```
public class	MainActivty extends AppCompatActivty{
	@Override
	protected void onCreate(Bundle saveInstanceState){
	suepr.onCreate(saveInstanceState);
	setContextView(R.layout.acivity_main);
	//other code  to setup the activity
	}
	//other code
}
```

####布局
1. 三大常用布局：帧布局、线性布局、约束布局

####foreach
基本语法

```
for(Type w:ObjectName){
	w.method();
}
```
####Android Monitor
常见的信息（严重程度由下至上增加）

- ERROR

用于记录明显的错误

```
log.e(String tag,String message)
```
- WARN

不会使应用出现错或崩溃

```
log.w(String tag,String message)
```

- INFO

纯信息性的消息

```
log.i(String tag,String message)
```

- DEBUG
- VERBOSE



