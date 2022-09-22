## 为什么需要WebViewTool？
* 添加依赖，一行代码快速访问外部网页。
* 定制版本，和网页做特定的交互。

## 说明：
* 此工具类是自用的定制版本。

##   以下是WebViewTool的集成、使用教程:
Step 1.先在 build.gradle(Project:XXXX) 的 repositories 添加:
```javascript
allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}
  ```
  
  Step 2. 然后在 build.gradle(Module:app) 的 dependencies 添加:
  ```javascript
  dependencies {
  		implementation 'com.github.ljw124:WebViewTool:1.0.1'
	}
	
```
 
  Step 3. 在需要访问网页时调用(一般是点击扫码图标):
  ```javascript
  startActivityForResult(new Intent(MainActivity.this, CaptureActivity.class), CaptureActivity.REQUEST_CODE);
  ```
  
  step 4. 在onActivityResult方法中接收扫码识别的结果:
  ```javascript
  @Override
    protected void onActivityResult(int requestCode, int resultCode, @Nullable Intent data) {
        super.onActivityResult(requestCode, resultCode, data);
        if (requestCode == CaptureActivity.REQUEST_CODE && resultCode == CaptureActivity.RESULT_CODE && null != data) {
            Bundle extras = data.getExtras();
            String msg = extras.getString("msg").trim();
        }
    }
    ```
 
