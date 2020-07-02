## 链游玩家游戏中心SDK  iOS版本
## 介绍
链游玩家游戏中心SDK提供游戏中心界面。

## 项目集成
此SDK依赖第三方穿山甲SDK
如果宿主工程没有集成穿山甲SDK,请先集成穿山甲SDK，成功之后，再继续后续操作。

ThreeLib文件夹中 BUAdSDK 文件夹即为穿山甲SDK,可直接导入，或者删除BUAdSDK 文件夹,按照穿山甲官网提示操作（穿山甲SDK地址：https://partner.oceanengine.com/union/media/union/download）
如果直接使用ThreeLib文件夹中 BUAdSDK文件夹拖入，需添加以下依赖库：
```
工程需要在TARGETS -> Build Phases中找到Link Binary With Libraries，点击“+”，依次添加下列依赖库
StoreKit.framework
MobileCoreServices.framework
WebKit.framework
MediaPlayer.framework
CoreMedia.framework
CoreLocation.framework
AVFoundation.framework
CoreTelephony.framework
SystemConfiguration.framework
AdSupport.framework
CoreMotion.framework
Accelerate.framework
libresolv.9.tbd
libc++.tbd
libz.tbd
libsqlite3.tbd
如果以上依赖库增加完仍旧报错，请添加ImageIO.framework。

```
穿山甲sdk接入成功后
将LYGCApi 、ThreeLib 文件夹拖进项目 （ThreeLib文件夹中 BUAdSDK 文件夹是穿山甲SDK，请注意不要二次拖入）
```
在Build Settings , Other Linker Flags 加入 -ObjC
```
在info.plist 如下配置：

1.配置网络
```
App Transport Security Settings
Allow Arbitrary Loads    YES

```

在AppDelegate 加入下列代码
```
AppDelegate.h 内添加
@property (strong, nonatomic) UIWindow *window;

```


## 代码使用
在`AppDelegate.h`导入头文件：
```
#import <LYGameCenterSDK/LYGCSingletion.h>

```
初始化SDK 在应用的 `Application` ` didFinishLaunchingWithOptions
 ` 方法中 初始化下方代码  `setDebug` 方法开启sdk debug 和 release模式 （请先设置模式再初始化代码）
 ， 初始化参数一是链游玩家平台分配的 `appid` 参数二是链游玩家平台分配的 `key`， 参数三是用户账户`account`，参数四是用户昵称`nickname`，参数五是用户性别`sex`(传数字：1男2女)，参数六是用户头像`headerimgurl`
```
     //1.先设置 环境 
    [[LYGCSingletion sharedManager] setDebug:YES];
    //2.初始化sdk (性别传 1 男，2 女)
    [[LYGCSingletion sharedManager] lycg_initSdkwithAppid:@" xxx " withKey:@" xxx " withAccount:@" xxx " withNickname:@" xxx " withSex:@"2" withHeadimgurl:@" xxx "];
    
  ```
##### 游戏中心

```
 导入头文件
#import <LYGameCenterSDK/LYGameCenterViewController.h>
 
 LYGameCenterViewController * centerView = [[LYGameCenterViewController alloc]init];
 UINavigationController * nav = [[UINavigationController alloc]initWithRootViewController:centerView];
 nav.modalPresentationStyle=UIModalPresentationOverCurrentContext;
 [self presentViewController:nav animated:YES completion:nil];
  
```
 
## 冲突
如果有三方库冲突，请直接移除ThirdLib文件夹中对应的三方库 





