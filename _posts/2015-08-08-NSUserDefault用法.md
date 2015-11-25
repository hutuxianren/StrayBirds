---
layout: post
title: NSUserDefaults
category: iOS技术
comments: true
---
##NSUserDefault standardUserDefault的使用
  本地存储数据简单来说有三种方式:数据库、NSUserDefaults和文件(如info.plist)
  NSUserDefaults用于存储数据量小的数据，例如用户配置。并不是所有的东西都能往里放，只支持:NSString、NSNumber、NSDate、NSArray、NSDictionary
  详细的方法可以查看类文件。
  NSUserDefaultsstandardUserDefaults用来记录一下永久保留的数据非常方便，不需要读写文件，而是保留到一个NSDictionary字典里，由系统保存到文件里，系统会保存到该应用下的/Library/Preferences/gongcheng.plist文件中。需要注意的是如果程序意外退出，NSUserDefaultsstandardUserDefaults数据不会被系统写入到该文件，不过可以使用［[NSUserDefaultsstandardUserDefaults] synchronize］命令直接同步到文件里，来避免数据的丢失。
  - 将数据存储到NSUserDefaults：

<pre><code>
    - (IBAction)switchChanged:(id)sender{

        NSUserDefaults *userDefaults = [NSUserDefaults standardUserDefaults];

        [userDefaults setBool:_theSwitch.on forKey:@"switchValue"];

}
</pre></code>

<pre><code>
- (IBAction)inputChanged:(id)sender{

        NSUserDefaults *userDefaults = [NSUserDefaults standardUserDefaults];

        [userDefaults setObject:_textField.text forKey:@"inputValue"];

}
</pre></code>


- 读取NSUserDefaults中的数据：

UISwitch
<pre><code>
NSUserDefaults *userDefaults = [NSUserDefaults standardUserDefaults];
BOOL sw = [userDefaults boolForKey:@"switchValue"];[_theSwitch setOn:sw];
</pre></code>
//UITextField
<pre><code>
NSString *str = [userDefaults stringForKey:@"inputValue"];[_textField setText:str];
</pre></code>
