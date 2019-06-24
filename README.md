

## 基础配置
引入包文件

`$ npm install react-native-microutil --save`

`$ react-native link react-native-microutil`

执行完这两句之后，直接在使用文件地址引入；



## 一、打开浏览器跳转对应链接（默认浏览器）
调用方法：
```javascript
import RNMicroutil from 'react-native-microutil';

RNMicroutil.openLink(linkAddress);  //linkAddress:需打开链接地址  
````

## 二、唤醒APP 

### iOS >>>>>>>>>>>>>>
1、需配置iOS白名单 
   
修改./ios/你的项目/info.plist

添加以下内容

    <!-- 第三方APP白名单 -->
    
    <key>LSApplicationQueriesSchemes</key>
    <array>
        <string>wexin</string>
        <string>alipay</string>
    </array>
    


2、js调用

```javascript

import RNMicroutil from 'react-native-microutil';

RNMicroutil.openApp(appName);  

//appName:对应APP名称   目前只有微信（weixin）、支付宝（alipay）
 
````

### Android >>>>>>>>>>>>>>>>>>

正常使用js调用

```javascript

import RNMicroutil from 'react-native-microutil';

RNMicroutil.openApp(appName);  

//appName:对应APP名称   目前只有微信（weixin）、支付宝（alipay）
 
````




## 三、获取设备信息

### 注意： 需先运行 npm link react-native-device-info

### iOS >>>>>>>>>>>>>>

参考链接：https://www.npmjs.com/package/react-native-device-info

1、首先在xcode中进行初始化

打开xcode，找到自己的项目->Libraries文件夹，选择Add Files to '项目名'，然后找到当前项目目录/node_modules/react-native-device-info文件夹，找到'RNDe'viceInfo.xcodeproj'文件，然后点击Add.



2、再在xcode中加载内库

找到项目名字 ----> Build Phases ---> Link Binary With Libraries, 点击‘+’按钮，添加‘libRNDeviceInfo.a’库。



3、继续添加环境变量

找到项目名字 ----> Build Setting ---> Header Search Paths  增加以下两个环境变量

$(SRCROOT)/../react-native/Reactand

$(SRCROOT)/../../React

并修改recursive.


4、js调用
```javascript
import RNMicroutil from 'react-native-microutil';

const devices=RNMicroutil.getDevice();  

devices.getUniqueID();  //API参照官方


````

### Android >>>>>>>>>>>>>>>>>>

正常使用js调用
```javascript

import RNMicroutil from 'react-native-microutil';

RNMicroutil.getDeviceInfo();  //API参照官方


````
