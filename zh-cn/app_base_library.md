* Eros工程基础库（包含）
  * 拓展的 weex 不具有的 `module`。
  * 拓展的 weex 不具有的 `component`。
  * 拓展的`简易更新逻辑`。
  * 内置了 `WeexSDK`。
  * ...持续优化中

Eros 基础库是必须依赖的，初始化中的模板已经添加了基础库的依赖，用户需要关心的是升级基础库，通过插件的方式升级也很简单，只需要修改一下版本号即可，集成方式中有介绍；

## 集成方式

**iOS 集成** <br>
* 打开iOS目录`工程目录/platforms/ios/WeexEros`，编辑Podfile文件，修改版本号（即 tag对应的版本号），库每次升级后都会有相关说明文档详情请看页面最下方的 Change Log，如需升级将 tag 修改为对应的版本即可；
	```ruby
	def common
    	...忽略其他库的引用
       #集成 Eros iOS 基础库
    	pod 'BMBaseLibrary', :git => 'https://github.com/bmfe/Benmu-iOS-Library.git', :tag => '版本号'
	end
	target 'WeexEros' do
    	common
	end
	```

* 在终端中`cd`到此目录下执行 `pod update`，就会重新拉取最新版本的文件，等待命令执行完毕即可；

**Android 集成**

* 打开Android目录`工程目录/platforms/android/WeexFrameworkWrapper/app`,编辑app目录下build.gradle 文件 `dependencies` 下添加引用，代码如下：

	```ruby
	dependencies {
		....
		implementation 'com.github.bmfe.eros-nexus:nexus:0.0.6'
    		implementation 'com.github.bmfe:WeexErosFramework:0.0.6'
	}
	```
>  ":"后面的 0.0.6 是版本号， 如需要更新 修改对应版本即可
* 添加完后，右上角 有一个 sync now。 点击 等待同步完成没有报错证明组件添加成功

## Change Log

**iOS 1.2.2**<br>

* 修复热更新后，新增加的页面提示找不到的问题;
* 优化webview加载时机，提升加载速度；
* 修复日历单选模式重复点击一天样式显示的问题；
