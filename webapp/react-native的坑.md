#### 一、真机测试-unable to load script 坑
- 报错：unable to load script from assets 'index.android bundle'  ,make sure your bundle is packaged correctly or youu're runing a packager server
- 解决方法：
1. 在  android/app/src/main 目录下创建一个  assets空文件夹
2. 执行 下面这段命令：（多出两个文件夹）
```
react-native bundle --platform android --dev false --entry-file index.android.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res/  
```
3. 重新run程序：react-native run-android