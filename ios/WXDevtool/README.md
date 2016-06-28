# WXDevtool
Remote debug for your native iOS app using Chrome Developer Tools

## weex-devtool启动：

0. 启动weex-devtool

	0. $:npm install -g weex-debugger

	0. $:weex-devtool  

		执行完会显示native需要链接的ws地址,之后自动打开chrome 。
		
		如果提示weex-devtool报错,建议升到6.0以上,可用如下命令升级：
		
		$:npm install -g n
		
		$:n latest
		
		
## playground安装WXDevtool
0. $:pod install
    
    更新pod依赖库

### native 调用 
0. inspect调试
	* AppDelegate.m文件引入头文件 #import "WXDevtool.h"
	* 程序启动时调用 
	
			+(void)launchInspectorWithSocketUrl:(NSURL *)url
		url为terminal显示的ws地址。

	 		eg：- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
			{//launch inspector
			  [WXDebugTool launchInspectorWithSocketUrl:			[NSURL URLWithString:@"ws://		30.30.29.242:8088/debugProxy/native"]];
			}

	 
	* 启动app，此时chrome页会显示你的设备与app name，选择启动inspector开启调试模式
	* 日志实时打印支持不同级别打印。
	
			eg：PDLogE()/PDLogW

0. debugger调试
	* 程序启动时调用
	
		  (void)launchDebugWithSocketUrl:(NSString *)url;
	 
	 	  eg：-(BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
			{//launch debug
    		[WXDebugTool launchDebugWithSocketUrl:@"ws://			30.30.29.242:8088/debugProxy/native"];
			}

	* 启动app，此时chrome页会显示你的设备与app name，选择启动debugger开启调试模式
	
### WXDevtool Dependencies

* libicucore.dylib
* CFNetwork.framework
* CoreData.framework
* Security.framework
* Foundation.framework

**注：当前版本inspect与debug要分开调试，下个版本实现同时调试**



￼