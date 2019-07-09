# MSLaunchView
### 一键合成APP引导页，包含不同状态下的引导页操作方式，同时支持动态图片引导页和静态图片引导页,支持按钮跳过按钮，立即体验按钮完全自定义,PageControl样式多样（支持方形点，圆形点，横线+小圆点样式等),省掉冗余的代码,集成性高,使用方便;
---
#### 声明:部分图片来源于网络,如有涉及版权会马上删除,敬请谅解; 

### 效果图展示：
#### APP静态图片引导页(上) | APP动态图片引导页(下)
<table>
<tr>
<th>手动进入体验</th>
<th>自动进入体验</th>
</tr>
<tr>
<td><img src="https://github.com/lztbwlkj/MSLaunchView/blob/master/Demo/MSLaunchView/DesignSketchGIF/Untitled-1.gif" width="300"></td>
<td><img src="https://github.com/lztbwlkj/MSLaunchView/blob/master/Demo/MSLaunchView/DesignSketchGIF/Untitled-2.gif" width="300"></td>
</tr>
<tr>
<th>手动进入体验</th>
<th>自动进入体验</th>
</tr>
<tr>
<td><img src="https://github.com/lztbwlkj/MSLaunchView/blob/master/Demo/MSLaunchView/DesignSketchGIF/Untitled-6.gif" width="300"></td>
<td><img src="https://github.com/lztbwlkj/MSLaunchView/blob/master/Demo/MSLaunchView/DesignSketchGIF/Untitled-7.gif" width="300"></td>
</tr>    
</table>

#### 更新记录：
2019.07.09 -- v0.0.9 \
1、添加PageControl更多定义属性；\
2、PageControl支持Pod自动管理；\
3、新增最后一页是否隐藏PageControl属性(lastDotsIsHidden)；
 2019.06.22 -- v0.0.8 \
 1、添加更多“跳过”按钮属性；\
 2、添加App是否是首次打开的宏定义；\
 3、微调初始化方法，是否测滑消失你说了算；\
 4、增加引导页隐藏后的回调方法； 
 
 2019.01.05 -- v0.0.7:提交0.0.7版本 \
 1、添加PageControl更多的自定义属性;


#### 使用方式（支持代码创建和StoryBoard创建项目）:

##### 图片数组（gif自动识别）:

###### 使用代码创建的项目,无进入立即按钮:
```objc
MSLaunchView *launchView = [MSLaunchView launchWithImages:imageNameArray isScrollOut:YES];
```

###### 使用StoryBoard创建的项目,无进入立即按钮:
```objc
MSLaunchView *launchView = [MSLaunchView launchWithImages:imageNameArray sbName:@"" isScrollOut:NO];
```

###### 使用代码创建的项目,有进入立即按钮:
```objc
MSLaunchView *launchView = [MSLaunchView launchWithImages:imageNameArray guideFrame:rt gImage:[UIImage imageNamed:@""] isScrollOut:NO]；
```


###### 使用StoryBoard创建的项目,有进入立即按钮:
```objc
MSLaunchView *launchView = [MSLaunchView launchWithImages:imageNameArray sbName:@"" guideFrame:rt gImage:[UIImage imageNamed:@""] isScrollOut:YES]；
```

##### 小视频（目前仅支持单个视频文件）:
```objc
NSString *path  = [[NSBundle mainBundle]  pathForResource:@"测试" ofType:@"mp4"];
NSURL *url = [NSURL fileURLWithPath:path];
[MSLaunchView launchWithVideo:CGRectMake(0, 0, MSScreenW, MSScreenH) videoURL:url];
```

==！！！如果你使用带立即进入按钮的初始化方法，那么后面的guideBtnCustom:方法将会失效！！！==

##### 视频的用法和图片的用法基本一致 这里就不再赘述,具体请参考Demo

### 集成方式:
#### 1.下载项目或者下载项目中MSLaunchView文件夹,将下载好的文件拖拽到自己的工程文件夹中,并在AppDelegate.h中导入#import "MSLaunchView.h"头文件;

#### 2. cocoapods集成:
###### 在项目的podfile文件中加入下面代码
```objc
pod 'MSLaunchView', '~>0.0.5'
```

#### 你还可以进行简单设置:
```objc
launchView.guideTitle = @"";
launchView.guideTitleColor = [UIColor redColor];

//是否隐藏跳过按钮
launchView.isHiddenSkipBtn = YES;
//PageControl属性
launchView.nomalColor = [UIColor lightGrayColor];
launchView.currentColor = [UIColor orangeColor];

//视频拉伸方式
launchView.videoGravity = AVLayerVideoGravityResize;
//播放完成是否自动推出 默认:YES
launchView.isPalyEndOut = NO;

```

#### 自定义按钮:
###### 自定义立即进入按钮:
```objc
[launchView guideBtnCustom:^UIButton * _Nonnull{
UIButton *btn = [UIButton buttonWithType:UIButtonTypeCustom];
btn.frame = CGRectMake(60, 60, 120, 120);
[btn setBackgroundColor:[UIColor redColor]];
[btn addTarget:self action:@selector(hidde) forControlEvents:UIControlEventTouchUpInside];
return btn;
}];

-(void)hidde{
[_launchView hideGuidView];
```

###### 自定义跳过按钮:
```objc
[launchView skipBtnCustom:^UIButton * _Nonnull{
UIButton *btn = [UIButton buttonWithType:UIButtonTypeCustom];
btn.frame = CGRectMake(60, 200, 120, 120);
[btn setBackgroundColor:[UIColor blueColor]];
[btn addTarget:self action:@selector(hidde) forControlEvents:UIControlEventTouchUpInside];
return btn;
}]；

-(void)hidde{
[_launchView hideGuidView];
}
```


## <<分享是一种美德,你的Star是我更新的动力，使用过程如果有什么问题可以[issues](https://github.com/lztbwlkj/MSLaunchView/issues/new),我会及时回复大家！>>


