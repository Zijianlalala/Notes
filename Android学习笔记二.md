# Android学习笔记二
## 获取URL
```
package com.example.android.datafrominternet.utilities;
import java.net.URL;
import android.net.Uri;
//省略其他import
public class NextworkUtils {
	//几个固定不变的量
	final static String GITHUB_BASE_URL = 
	"https://api.github.com/search/repositories";
	final static String PARAM_QUERY = "q";
	final static String PARAM_SORT = "sort";
	final static String sortBy = "starts"; 
	
	public static URL buildUrl(String searchQuery) {
		Uri buildUri = Uri.parse(GITHUB_BASE_URL).buildupon()
		.appendQueryParameter(PARAM_QUERY,searchQuery)
		.appendQueryParameter(PARAM_SORT,sortBy);
		URL url = null;
		try {
			url = 	new URL(buildUri.toString());
		}catch(MalformedURLException e) {
			//URL格式不正确异常
			e.printStackTrace();
		}
		return url;
	}
}
```
最后形成的URL为：
`https://api.github.com/search/repositories?q=searchQuery&sort=stars`
## 将inputStream转化为String的方法
```
static String convertStreamToString(java.io.InputStream is) {
	java.util.Scanner s = new java.util.Scanner(is).useDelimeter("\\A");
	return s.hasNext() ? s.next() : "";
}
```
## 在AndroidManifest中添加权限

```
<uses-permission android:name="android.permission.INTERNET"/>
```
## AsyncTask
#### 定义
android提供的轻量级的异步类，适用于简单的异步处理

#### UI线程可以接受三种类型的参数

1. Params 启动任务执行的输入参数，比如HTTP请求中的URL
2. Progress 后台任务执行的百分比
3. Result 后台执行任务最终返回的结果

#### 异步加载数据的方法
1. doInBackground(Params..):异步执行后台线程将要完成的任务
2. onPreExecute:执行后台耗时操作之前被调用，通常用户完成一些初始化操作
3. onPostExecute(Result)：当doInBackground(Params..)方法执行完成后，系统自动调用该方法，并将doInBackground(Params..)的返回值传给该方法
4. onProgressUpdate()：doInBackground更新任务的执行进度后，触发该方法
