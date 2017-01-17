# SwiftSmallNote
- UILabelView的自动获取高度(label.sizeThatFits()),这个函数虽然会自动获取label上文本的高度，但是英文和中文的字体高度是不同的，所以需注意
- UIImageView加载图片时，如果是用(named:"xxx")加载，那加载的图片会被放在缓存里，并且这块缓存区的数据，并不会遵循ARC内存管理方式，也就是说即使目前应用没有任何拥有该内存区域的对象了，这块内存区域也不会被释放，只有当应用周期结束（应用退出），该内存区域才会被释放。所以当加载不必要的图片时，建议使用(contentsOfFile:)
- 在tableView内容比较少时，可以不用重用机制http://www.faceye.net/search/82604.html#bottom-ad
- 图标问题，使用图标的时候，所选取的图标最好于app里的图标大小接近，否则可能会存在锯齿
- 虽然我比较喜欢使用tableView来做长内容的显示，但真相是，使用scrollerView可能会更优。
- storybord肯定是一个好工具，只是我还没会充分的使用
- tag是一个标记控件的好办法，这样可以让你更好的找到你想要找的控件
- 使用使用系统闭包反向传值会有延迟
- static 的属性和全局变量默认都是懒加载的
- struct(值传递)，class(引用类型)，往往使用引用类型会对性能有很大的提高(因为应用类型是引用地址)
- table的Cell的一致性可能会比较重要，如果其他的cell都是可以可以点击的，但是有一个cell是不可以点击的，那tablleView就可能回出项卡顿(是不是这个原因还有待排查)
- iOS蓝牙方面的文章，没仔细看，但是从评论上来看，应该写得不错，以后再看http://www.jianshu.com/p/87c30628ddaa
- 当控件加了阴影，并且你在执行的画的时候，可能回照成卡顿，解决的办法，可以在加阴影之前加上这一句来描述控件的边界xxx.layer.shadowPath = UIBezierPath(rect:self.bounds).cgPath http://blog.csdn.net/mkhgg/article/details/7286282
- 地图标注一定会有一个值是固定不变的，称为标注点。当我们自己重定义标注时，应注意偏移量。
- 地图请求路线的操作是一个回调闭包，是异步操作，顺序是由请求的服务器的响应时间决定的，不是由你请求的顺序决定的
- 在使用地图进行路线请求时，如果请求的点不在道路上，那就可能造成路线的点与标注点不重合。
- xcode8兼容8.0以下的系统http://blog.csdn.net/CodingFire/article/details/52638265 (但是有一个问题，就是你不是开发者账号，就是付费账号，你是不能添加新的设备)
- All interface orientations must be supported unless the app requires full screen.这个警告信息的解决方法是General->Deployment Info->勾选Requires full screen(http://stackoverflow.com/questions/31141806/xcode-7-beta-warnings-interface-orientations-and-launch-storyboard)
- 给navigation设置title时，要把这项设置放在其他navigation设置之后(这个说法是错的。。。。刚刚发现是自己的bug。。。)
- UIlable可以借助addAttribute属性来对一段文字附上不同的颜色
- 一些比较好的注意事项(我犯了其中的多数错误)http://www.cocoachina.com/ios/20161025/17849.html
- 对于项目中的重复代码，如果这个代码是用来处理基础类型的(string，int，cgfloat等)，那可以使用extension来扩展该类型
-  移除数组中的指定值，使用filter比较好(有一个数组ary:[String] = ["qin","zi","xuan"],当我想把"zi"去掉，可以这样使用filter：ary = ary.filter({$0 != "zi"}))
- 泛型是一个很好的特性，在以后的代码中我要多次尝试。
- 在项目中，必须确保资源库是现场安全的
- 对于iOS10，当我们需要用到一些权限时，需要在info文件中进行配置http://cc.cocimg.com/api/uploads/20161024/1477275020733377.png
- 如果在sb种想把静态tabelView放在自己定义的viewController中，会发生错误。解决办法：1：先往自己的viewController中添加一个Container View(拖入Container View后，系统会自动生成一根连线和一个新的ViewController) 2：把系统自动生成的东西都删掉 3：拖入一个新的tabelViewController，并从Container View中右键拉出线指向新的tabelViewController，选择Embed
- 关于自定义navigation的高度，可以看看这个博客http://www.cnblogs.com/wangyang1213/p/5308664.html
- 字体模糊的完全解决，妈的，控件的起始点必须是整数，起始点
- 聊天界面的对话框应该使用.9图片作为气泡背景
- 使用自己画线时，回产生线短粗细问题
- 当需要同时执行多个任务，并发队列是非常有用的。
- 但需要某些人物以指定的顺序去执行时，串行队列是一个非常好的选择
- 如果要修改navigation的全局属性，比如title的颜色，必须要在第一个navigation种设置。或者，在每个controller的viewWillAppear中设置
- 我的笔记本电脑显示的颜色和我外接显示器的颜色有点不一样
- 因为swift的init只会调用一次，因此在init中我们可以为常量进行赋值
- 因为iOS上的内存紧张，很有可能当你的应用程序被挂起进入后台后，被另一个需要消耗很大内存的应用挤掉(一个被挂起的应用程序不会运行任何代码，因此当他在挂起状态下被终止时，不会得到通知)，因此，当我们的应用程序被告知应用即将进入后台时，必须保存所以关键数据。
- 当应用程序被挂起或被唤醒时不会得到通知，但是当他被移入和移除后台时会得到通知
- 创建一个新队列不一定能创建一个新线程
- shadowOffset = size(width:3,height:-3)  //阴影形状向右移3，向上移3
- player.rate = 0.5 设置播放速率为0.5
- NSDateFormatter是一项成本相当高昂的操做，如果需要设置大量日期的格式，可以创建一个NSDateFormatter并将其保存下来，而不是每次需要格式化一个日期时都创建一个新的
- 如果没有动态特性需求的话，保持在swift基本类型中会让我们得到更多的性能提升
- 在iOS10/xcode8中，当使用rsa加密算法时出现的空值错误，需要到prj->Capabilities->keychain sharing中选择NO
- 可以使用Instruments工具查看内存是否泄漏
- Instruments工具的使用：运行程序->Debug Session->Memory->Profile in Instruments
- 不通过按钮来调用按钮的响应函数:buttonAction(button as! UIButton),有参时
- 初始化固定内容数组时可以采用lazy的初始化方式
- 移除所有按钮(可拓展为某个控件)xx = subviews.map{if $0.classForCoder == UIButton.classForCoder() {$0.removeFromSuperview()}}
- a??1 //如果a为nil，返回1，否则返回a
- 使用convenience关键字可以复写多个父类中的init
- 使用16进制来表示颜色：view.backgroudColor = UIColor.hexInt(0xf3f3f3)//这个要自己实现
- 在回调使用中，在闭包头加上[unowned self]
- 看到一篇关于描述“线程”和“进程”的文章，个人认为写得比较通俗易懂http://www.ruanyifeng.com/blog/2013/04/processes_and_threads.html
- 拓展swift的协议方法后，可以直接在遵循该协议的class中调用拓展的协议方法
- 是navigationBar变透明，并把下端的那条黑线去掉
```Swift
let img = UIImage()
self.navigationController.navigationBar.setBackgroundImage(img,for:.default)
self.navigationController.nacigationBar.shadowImage = img
self.navigationController.navigationBar.barStyle = .blackOpaque
```

- 在iOS10设备上出现的键盘第一次弹起时获取的高度不对的问题，使用下面代码可以获得正确的高度(FUCK,有问题)
```Swift
let keyInfo = (notification as NSNotification).userInfo![UIKeyboardFrameEndUserInfoKey]
let height:CGFloat = (keyInfo! as AnyObject).cgRectValue.size.height//(origin.y)
```

- tableView.reloadData()后想让tableView滑至最低端
```Swift
（有问题）
let sectionCout:Int = self.contentTableView.numberOfSections
        if sectionCout != 0 {
            let rowC = self.contentTableView.numberOfRows(inSection: 0)
            if rowC != 0 {
                let ii = [0,rowC-1]
                let indexPath = NSIndexPath.init(indexes: ii, length: ii.count)
                self.contentTableView.scrollToRow(at: indexPath as IndexPath, at: .bottom, animated: false)
            }
        }
     
（新方法）
self.contantTableView.setContentOffset(CGPoint(x:0,y:self.contantTableView.frame.height),animated:false)
```

- 使用stack装载图片时，需要先把约束建立好，再设置stackView中的Distribution为Fill Equally
- 在使用autolayout和约束进行布局时，如果要对某个对象添加阴影，应该在veiwWillLayoutSubviews中添加(其他的layout属性也是这样)
- 在使用autolayout和约束进行布局时，如果要对cell添加阴影，在draw()中调用绘制阴影(因为UITableCell也是继承view的，所以每当启动cell时，就会调用draw函数，这样就避免了cell的长度大小不正确的问题)
- 使用guard(守卫来检查text的输入值并转型后赋值给使用变量):
```Swift
guard let text = xxxx.text , let xxxText = Int(text) else {
        print("error")
        return
}
```

- 猫神写的延时操作，记录下：
```Swift
func delay(_ timeInterval:TimeInterval,_ block: @escaping () -> Void) {
        let after = DispatchTime.now() + timeInterval
        DispatchQueue.main.asyncAfter(deadline:after,execute:block)
     }
```

- 可以通过widget来增加程序的互动性
- 约束可以像控件一样拖入代码区然后进行属性修改
- 当改变约束属性，并且想实现动画效果时，需要加上view.layoutIfNeeded()
- 让textView从开头开始显示
```Swift
self.textView.scrollRangeToVisible(NSRange(location:0,length:1))
```

- 关于alamofire的get请求中中文问题：http://blog.csdn.net/u014134886/article/details/50997803
```Swift
//错误示例
 let url : URLStringConvertible = "http://bai.com/test2/login/get.php?mobile=\(userPhone)&rename=\(username)"

//正常示例
 let url : URLStringConvertible = "http://baidu.tk/test2/login/register.php"
            let para=["mobile": userPhone,""rename": username];
            Alamofire.request(.GET, url ,parameters: para).responseJSON{ response in
                if let JSON = response.result.value
                {
                    if JSON["msg"] as! String == "1"
                    {
                        self.registerActivity.stopAnimating()
                        //self.dismissViewControllerAnimated(true, completion: nil)
                        self.showAlert("成功", alertMessage: "成功，请返回", actionTitle: "确定")
                       self.navigationController?.popViewControllerAnimated(true)
                    }
                    else
                    {
                        self.registerActivity.stopAnimating()
                        self.showAlert("出错", alertMessage: "", actionTitle: "确定")
                    }
                }

            }
```

- 改变点击cell时的高亮颜色
```Swift
let tapCellColor:UIColor = UIColor(red:96/255,green:54/255,blue:12/255,alpha:1.0)
cell.selectedBackgroundView = UIView(frame:cell.frame)
cell.selectedBackgroundView.backgroundColor = tapCellColor
```

- 设置navigation的title，以及设置返回键和title的颜色
```Swift
self.navigationItem.title = "xxx"//设置标题
self.navigationController.navigationBar.titleTextAttributes = [NSForegroundColorAttributeName:UIColor]//设置title的颜色
self.navigationController.navigationBar.tintColor = UIColor//设置返回键的颜色
```

- 自适应内容的label(使用sizeThatFites和sizeToFit)
```Swift
let label = UILable(frame:CGRect(x:100,y:100,width:0,height:0))
label.font = UIFont.systemFont(ofSize:20)
label.text = "hello label"
label.sizeToFit()
```

- 帧数计算方法(使用CADisplayLink)
```Swift
var lastTime:TimeInterval = 0
var count:Int = 0

//每当屏幕刷新时都会调用tick函数(60帧就是在1秒内调用60次tick)
let disPlayLink = CADisplayLink(target:self,selector:#selector(tick))
disPlayLink.add(to:RunLoop.main,forMode:.commonModes)

func tick(link:CADisplayLink) {
    //判断是不是第一次进入该定时函数
    if lastTime == 0 {
        lastTime = link.timestamp       //把当前的时间戳存入lastTime中
        return
    }
    count += 1  //记录刷新的次数
    let delta:TimeInterval = link.timestamp - lastTime  //把当前时间戳与上一段时间戳进行比较
    if delta < 1 {      //当delta小于1时，说明还没到1秒的时间
        return
    }
    
    lastTime = link.timestamp   //更新时间戳
    let fps = Double(count) / dalta     //刷新次数 / 时间 = 帧数
    let fpsText = Int(round(fps))       //取整后转为Int型
}
```

- 两种获取Document目录的方法
```Swift
one: 
let fileManager = FileManager.default
let urls = fileManager.urls(for:.documentDirectory,in:.userDomainMask)
let documentDirectory = urls[0] as NSURL
let addUrl = documentDirectory.appendingPathComponent("string")

two:
let docDir = NSSearchPathForDirectoiesInDomains(.documentDirectory,.userDomainMask,true)[0]
let addUrl = docDir + "String"
```

- 强制结束block动画
```Swift
例如，我对一个testView进行动画描述
UIView.animate(withDuration: 2, delay: 0, options: [.repeat,.autoreverse,.curveEaseInOut], animations: { 
            self.testView.alpha = 0
            }) { (finish) in
                if !finish {
                    self.testView.alpha = 1
                    return
                }
        }
当我想取消这个循环动画时，只需要在某个地方调用
self.testView.layer.removeAllAnimations()
调用完该方法后，上述动画中的finish就会取得一个false值，表示的是改动画不是正常结束
接着return就可以将之间邦在testView上的动画删除了
```
- 添加约束后的viewController初始化的执行顺序
```Swift
one:viewDidLoad//frame没有发生约束变化
two:viewWillLayout//frame没有发生约束变化
three:get{}//frame发生了约束变化
four:viewDidLayout//frame发生了约束变化
```

- 比较随机的随机数
```Swift
Int型：Int(arc4random_uniform(UInt32(200)))//0..<200
```

- 初始化控件的frame的方法
```Swift
1:CGRect.init(x:y:width:height:)
2:CGRect(x:y:width:height:)
3:CGRect(origin:size)
```

- 取得父类ui的属性
```Swift
self.superview......
```

- 使用色调，饱和度，亮度来设置颜色
```Swift
//最大值为1，当饱和度，亮度为1时，色调从0增加到1时，颜色从000~255255255
UIColor(hue:,saturation:,brightness:,alpha:)
```

- 传入两个闭包
```Swift
typealias funA = (_ inOne:Int , _ inTwo:Int) -> Void
typealias funB = (_ inOne:String) -> Int
func set(one:@escaping funA , two:@escaping funB) {
        
}
```

- 描述一段由CGMutablePath()控制的layer动画
```Swift
let animate:CAShapeLayer = CAShapeLayer()       //用来承接变化路径的实例
let path = CGMutablePath()      //创建一个可以变化的路径
path:
     .move()    //定义起点
     .addLine() //添加一条线
     .addCurve() //添加点控制的曲线
```

- collectionView的点击动画(这里是简单的变色动画)
```Swift
    self.collect.delaysContentTouches = false //不加上这句的话，只能长按变色
    func collectionView(_ collectionView: UICollectionView, didSelectItemAt indexPath: IndexPath) {

        print(indexPath.row)
    }
    
    func collectionView(_ collectionView: UICollectionView, didHighlightItemAt indexPath: IndexPath) {
        let cell = collectionView.cellForItem(at: indexPath)
        cell?.backgroundColor = UIColor.lightGray
    }
    
    func collectionView(_ collectionView: UICollectionView, didUnhighlightItemAt indexPath: IndexPath) {
        let cell = collectionView.cellForItem(at: indexPath)
        cell?.backgroundColor = UIColor.yellow
    }

```

- app生命周期内的系统相应(后台，前台，退出)
```Swift
func applicationWillResignActive(_ application: UIApplication) {
        // Sent when the application is about to move from active to inactive state. This can occur for certain types of temporary interruptions (such as an incoming phone call or SMS message) or when the user quits the application and it begins the transition to the background state.
        // Use this method to pause ongoing tasks, disable timers, and invalidate graphics rendering callbacks. Games should use this method to pause the game.
        print("resign") //app从前台进入后台时调用one
    }

    func applicationDidEnterBackground(_ application: UIApplication) {
        // Use this method to release shared resources, save user data, invalidate timers, and store enough application state information to restore your application to its current state in case it is terminated later.
        // If your application supports background execution, this method is called instead of applicationWillTerminate: when the user quits.
        print("enterBack") //app从前台进入后台时调用two
    }

    func applicationWillEnterForeground(_ application: UIApplication) {
        // Called as part of the transition from the background to the active state; here you can undo many of the changes made on entering the background.
        print("enterFore") //app从后台进入前台时调用one
    }

    func applicationDidBecomeActive(_ application: UIApplication) {
        // Restart any tasks that were paused (or not yet started) while the application was inactive. If the application was previously in the background, optionally refresh the user interface.
        print("become") //进入app时调用(app从后台进入前台时调用two)
    }

    func applicationWillTerminate(_ application: UIApplication) {
        // Called when the application is about to terminate. Save data if appropriate. See also applicationDidEnterBackground:.
        print("terminate")  //程序结束后调用
        while(true) {
            print("222222") //程序结束后依旧能有数据操作，则会给出一定的时间来提供数据操作
        }
    }
```

- 取得剪切板上的内容
```Swift
let copyContent = UIPasteboard.general.string
```

- 正则判断手机号码和邮箱
```Swift
    /// 判断该字符串是不是手机号码
    ///
    /// - returns: bool
    func isPhoneValue() -> Bool {
        let trueMask:String = "^1(3[0-9]|4[57]|5[0-35-9]|8[0-9]|7[0135678])\\d{8}$"
        let phoneMask = NSPredicate.init(format: "SELF MATCHES %@", trueMask)
        return phoneMask.evaluate(with: self)
    }
    
    /// 判断该字符串是不是邮箱
    ///
    /// - returns: bool
    func isEmailValue() -> Bool {
        let trueMask:String = "[A-Z0-9a-z._%+-]+@[A-Za-z0-9.-]+\\.[A-Za-z]{2,4}"
        let emailMask = NSPredicate.init(format: "SELF MATCHES %@", trueMask)
        return emailMask.evaluate(with: self)
    }
```

- 检测手机摇晃
```Swift
    override func motionBegan(_ motion: UIEventSubtype, with event: UIEvent?) {
        print("startMotion")
    }
    
    override func motionEnded(_ motion: UIEventSubtype, with event: UIEvent?) {
        print("endMotion")
    }
    
    override func motionCancelled(_ motion: UIEventSubtype, with event: UIEvent?) {
        print("cancellMotion")
    }
```
