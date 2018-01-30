# ASMagnifierManger
放大镜效果。可更改放大倍数和放大镜大小

### 特点介绍
* 放大镜效果
* 放大镜形状自定义
* 放大倍数自定义
* 放大镜可换图片
* 放大镜大小自定义
* 使用方便

### 方法介绍
```
typedef NS_ENUM(NSInteger, MagnifierStyle)
{
    /* 圆形放大镜*/
    MagnifierStyleCircular = 0,
    /* 方形放大镜 */
    MagnifierStyleSquare,
};

@interface ASMagnifierManger : NSObject
/* 放大镜的宽度  - 默认90*/
@property (nonatomic, assign) float magnifierWidth;
/* 放大镜的背景图 */
@property (nonatomic, strong) UIImage *magnfierBackImg;
/* 放大镜形状  -默认圆形 */
@property (nonatomic, assign) MagnifierStyle magStyle;
/* 放大镜放大倍数 -默认1.5  必须大于1*/
@property (nonatomic, assign) float magnification;

+ (instancetype)sharedInstance;
```
### 使用方法
1. 单个视图使用，需要ViewController实现以下方法，就可以实现默认放大镜效果
```
- (void)touchesBegan:(NSSet<UITouch *> *)touches withEvent:(UIEvent *)event {
    [[ASMagnifierManger sharedInstance] magnifier_touchesBegan:touches withEvent:event];
}
- (void)touchesMoved:(NSSet<UITouch *> *)touches withEvent:(UIEvent *)event {
    [[ASMagnifierManger sharedInstance] magnifier_touchesMoved:touches withEvent:event];
}
- (void)touchesEnded:(NSSet<UITouch *> *)touches withEvent:(UIEvent *)event {
    [[ASMagnifierManger sharedInstance] magnifier_touchesEnded:touches withEvent:event];
}
```
2. 整个项目使用放大镜功能
  需要将方法1的方法写在基类ViewController中即可，

3. 配置放大镜参数
```
    //放大倍数
    [ASMagnifierManger sharedInstance].magnification = 3.0;
    //放大镜为圆形
    [ASMagnifierManger sharedInstance].magStyle = MagnifierStyleCircular;
    //放大镜大小
    [ASMagnifierManger sharedInstance].magnifierWidth = 100;
```
### 提示
 具体使用请下载demo查看!
