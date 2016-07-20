# StartPage_Encapsulation
启动页封装
常见启动页单独封装，继承与UIView，附加在首页之上。
APP第一次启动弹出，第二次启动屏蔽。

使用方法：

引入头文件：
#import "hDisplayView.h"

在AppDelegate的didFinishLaunchingWithOptions方法中添加

    if (![[NSUserDefaults standardUserDefaults] boolForKey:@"everLaunched"]) {
        [[NSUserDefaults standardUserDefaults] setBool:YES forKey:@"everLaunched"];
        [[NSUserDefaults standardUserDefaults] setBool:YES forKey:@"firstLaunch"];
    }
    else{
        [[NSUserDefaults standardUserDefaults] setBool:NO forKey:@"firstLaunch"];
    }
    
    if ([[NSUserDefaults standardUserDefaults] boolForKey:@"firstLaunch"]) {
        // 这里判断是否第一次
        
        hDisplayView *hvc = [[hDisplayView alloc]initWithFrame:CGRectMake(0, 0, MainScreen_width, MainScreen_height)];
        
        [self.window.rootViewController.view addSubview:hvc];
        
        [UIView animateWithDuration:0.25 animations:^{
            hvc.frame = CGRectMake(0, 0, MainScreen_width, MainScreen_height);
            
        }];
        
    }
    
    替换图片：
    将"hDisplayView.m"中使用图片替换成自己图片名称，或者使用SDWebimage方法赋予请求链接请求图片。
    
