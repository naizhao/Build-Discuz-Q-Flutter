# Build-Discuz-Q-Flutter
Build Discuz! Q Flutter APP using GitHub Actions

# 自定义方法
修改`build.yaml`，把里面的`domain`和`appname`改为自己的Disucz! Q实际地址和APP的实际名字。

# 如何解决每次编译后Android的APK签名不一致
修改`.github/workflows/build.yml`把下面这行删掉
```
keytool -genkey -v -alias key -keystore android/android.keystore -keypass naizhao -storepass naizhao -keyalg RSA -keysize 4096 -validity 3650 -dname "CN=Discuz Q, OU=DNSPod, O=Tencent Cloud, L=ShenZhen, ST=GuangDong, C=CN"
```
然后换成这行
```cp ../android.keystore android/android.keystore````
最后，用下面的命令行生成一个`android.keystore`，放到代码库的根目录下就好了。
```
keytool -genkey -v -alias key -keystore android/android.keystore -keypass naizhao -storepass naizhao -keyalg RSA -keysize 4096 -validity 3650 -dname "CN=Discuz Q, OU=DNSPod, O=Tencent Cloud, L=ShenZhen, ST=GuangDong, C=CN"
```
最后代码结构如下
```
├── .github
│   └── workflows
│       └── build.yml
├── README.md
├── android.keystore
└── build.yaml
└── discuz-q-logo.png
```