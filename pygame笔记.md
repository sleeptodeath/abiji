PyGame是 SDL 库的 Python 包装器（wrapper）。SDL 是一个跨平台库，支持访问计算机多媒体硬件（声音、视频、输入等）。SDL 非常强大，但美中不足的是，它是基于 C 语言的，而 C 语言比较难懂，因此我们采用 PyGame 。
### 01 安装
1.管理员运行cmd
2.pip install pygame

### 02 最小开发框架

```PYTHON
import pygame
from pygame.locals import *
import sys

pygame.init() #初始化

#初始化显示窗口，第一个参数size是一个二元组，分别表示窗口的宽度和高度
screen = pygame.display.set_mode((600,  400)) 
 #设置窗口名字
pygame.display.set_caption("Pygame游戏之旅")

while True:
    for event in pygame.event.get(): #获取事件并逐类响应
        if event.type == pygame.QUIT: #Pygame中定义的退出事件常量
            sys.exit()
    pygame.display.update() #刷新屏幕
```

### 03 屏幕控制 pygame.display
#### 03.1 屏幕尺寸和模式

* pygame.display.set_mode(r=(0,0), flags=0)
    * r是游戏屏幕的分辨率，采用(width, height)方式输入
    * flags用来控制显示类型，可用|组合使用，常用显示标签如下：
        *  pygame.RESIZABLE 窗口大小可调
            pygame.VIDEORSIZE 窗口大小更改的事件
            获得event.size[0] event.size[1]  改变set_mode(size)
        * pygame.NOFRAME 窗口没有边界显示
        * pygame.FULLSCREEN 窗口全屏显示
            设置 K_ESCAPE退出
        * 注意：每种显示方式要配合相应的处理机制

* pygame.display.Info()  
    产生一个显示信息对象VideoInfo，表达当前屏幕的参数信息  
    在.set_mode()之前调用，则显示当前系统显示参数信息  
    参数很多，其中有两个十分重要，如下： 
    * current_w:当前显示模式或窗口的像素宽度
    * current_h:当前显示模式或窗口的像素高度


#### 03.2 窗口标题和图标
* display.set_icon(surface) #设置窗口的图标效果,图标是一个Surface对象
    icon = pygame.image.load(filename)
    display.set_icon(icon)
* display.set_caption(title, icontitle=None)      #title设置窗口的标题内容

* display.get_caption() #返回当前设置窗口的标题及小标题内容  
    返回结构为(title, icontitle)

#### 03.3 窗口感知和刷新
* display.get_active() #当窗口在系统中显示(屏幕绘制/非图标化)时返回True，否则返回False
    该函数可以用来判断是否游戏窗口被最小化  
    进一步，判断后可以暂停游戏，改变响应模式等

* display.flip()  #重新绘制整个窗口
* display.update()  #仅重新绘制窗口中有变化的区域，相比.flip()执行更快

### 04.主页面
screen.fill(color) #显示窗口背景填充为color颜色
screen.blit(src, dest) #将一个图像绘制在另一个图像上，即将src绘制到dest位置上。
### Surface 对象
surf = pygame.surface(())
surf.fill() # 设定Surface的颜色，使其和屏幕分离
surf.get_rect()
```PYTHON
# 创建Surface 并用原则设定它的长度和宽度
surf = pygame.Surface((50,50))
# 设定Surface的颜色，使其和屏幕分离
surf.fill((255,255,255))
#得到一个矩形区域和 Surface 的 x 轴 和 y 轴。
rect = surf.get_rect()
```

### Rect
pygame.Rect.move_ip(self, x, y) -> None
pygame.Rect.move(self, x, y)-> Rect

### 05.帧率和时间
fclock = pygame.time.Clock() #创建一个Clock对象，用于操作时间
fclock.tick(framerate) #控制帧速度，即窗口刷新速度

pygame.time.set_timer(eventid, milliseconds)->None repeatedly create an event on the event queue
    如果milliseconds 设置为0时，不进行事件
### 04.图片处理
pygame.image.load(filename) -> surface对象

img.get_rect()  -> Rect对象
### Sprites

pygame.sprites.Group()
    .add() Adds a sprite or sequence of sprites to a group.
    .draw()
    .clear()
    .update()
    .remove()
### 05.事件处理
event.pos[]
#### 系统
* QUIT
* ACTIVEEVENT
#### 键盘处理
    pygame.KEYDOWN
        event.unicode 一般不用
        event.key #按键的常量名称
            pygame.K_UP
            pygame.K_LEFT
            pygame.K_DOWN
            pygame.K_RIGHT
        event.mod #按键修饰符的组合值
            KMOD_NONE
            KMOD_LSHIFT
            KMOD_RSHIFT
            KMOD_SHIFT
            KMOD_CAPS
            KMOD_LCTRL
            KMOD_RCTRL
            KMOD_CTRL
            KMOD_LALT
            KMOD_RALT
            KMOD_ALT
            KMOD_LMETA
            KMOD_RMETA
            KMOD_META
            KMOD_NUM
            KMOD_MODE
    pygame.KEYUP

#### 鼠标处理
    MOUSEMOTION
        event.pos 鼠标当前坐标值(x,y)，相对于窗口左上角
        event.rel   鼠标相对运动距离(X,Y)，相对于上次事件
        event.buttons 鼠标按钮状态(a,b,c)，对应于鼠标的三个键
    MOUSEBUTTONUP
        event.pos  鼠标当前坐标值(x,y)，相对于窗口左上角
        event.button  鼠标按下键编号n 取值0/1/2，分别对应三个键, 左键为1
    MOUSEBUTTONDOWN 
        event.pos  鼠标当前坐标值(x,y)，相对于窗口左上角
        event.button 鼠标按下键编号n 取值为整数，左键为1，右键为3，设备相关
#### 游戏杆

#### 窗口
    VIDEORSIZE
    VIDEOREXPOSE
#### 用户定义
    USERENVENT...


### 事件处理函数
#### 处理事件
    pygame.event.get([type or typelist]) #从事件队列中获得事件列表，即获得所有被队列的事件
    pygame.event.poll() #从事件队列中获得一个事件  
        事件获取将从事件队列中删除
        如果事件队列为空，则返回event.NOEVENT
    pygame.event.clear([type or typelist]) #从事件队列中删除事件，默认删除所有事件

#### 操作事件队列 
    #设置事件队列能够缓存事件的类型
    pygame.event.set_blocked(type or typelist) #控制哪些类型事件不允许被保存到事件队列中
    pygame.event.get_blocked(type or typelist) #测试某个事件类型是否被事件队列所禁止 如果事件类型被禁止，则返回True，否则返回False
    pygame.event.set_allowed(type or typelist) #控制哪些类型事件允许被保存到事件队列中

#### 事件生成函数
    pygame.event.post(Event)  
        产生一个事件，并将其放入事件队列
        一般用于放置用户自定义事件（pygame.USEREVENT）
        也可以用于放置系统定义事件（如鼠标或键盘等），给定参数
    pygame.event.Event()
        创建一个给定类型的事件
        • 其中，事件的属性和值采用字典类型复制，属性名采用字符串形式
        • 如果创建已有事件，属性需要一致

### 色彩和绘图机制
#### 色彩
pygame.Color()  RGB/RGBA
    * Color(name)
    * Color(r, g, b, a)
    * Color() #8位十六进制 例如： Color ("#BEBEBE“)
    pygame.Color.r
    pygame.Color.g
    pygame.Color.b
    pygame.Color.a
    pygame.Color.normalize 将RGBA 各通道值归一到 0-1之
    
#### 图形 pygame.draw
pygame.draw.rect(surface, color, rect, width=0)
    Surface 矩形的绘制屏幕
    • color 矩形的绘制颜色
    • Rect 矩形的绘制区域
    • width=0 width=0 绘制边缘的宽度，默认为 0，
    x,y,w,h, width,height top,left, right, bottom
    rect.move(x, y)
pygame.draw.polygon(surface, color, pointlist, width=0)
    pointlist 多边形顶点坐标列表

.circle(surface, color ,pos, radius, width=0)
    pos 圆形的心坐标
    • radius 圆形的半径
    • width=0 绘制边缘的宽度，默认为 0，
.ellipse(surface, color, rect, width=0)
.line(surface, color, start_pos, end_pos, width=0)
.lines()
.aaline()
.aalines()
.arc()

#### 文字 
pygame.freetype 向屏幕上绘制特定字体的文字
import pygame.freetype

系统中的字体：
    Windows 系统 C: \Windows\Fonts
字体文件的扩展名
    *.ttf *. ttc

方法：
pygame.freetype.Font(file, size=0）
根据字体和字号生成 一个 Font 对象

Font.render_to(surf, dest, text, , fgcolor， bgcolor=None, rotation=0, size=0)
->Rect
    • surf 绘制字体的平面， Surface 对象
    • dest 在平面中的具体位置， (x,y )
    • text 绘制的文字 内容
    • fgcolor 文字颜色
    • bgcolor 背景颜色
    • rotation 逆时针的旋转角度，取值 0-359 ，部分字体可旋转
    • size 文字大小，赋值该参数将覆盖 Font

Font.render(text, , fgcolor， bgcolor=None, rotation=0, size=0)
-> (Surface, Rect)

用Font对象的 render*绘制具体文字

### 冲突检测
pygame.Rect.collidepoint(self, x, y) -> bool
pygame.Rect.colliderect(self, Rect) -> bool


### 声音处理
pygame.mixer.init()

Sound.set_volume(value)->None

#### 背景音乐
pygame.mixier.music.load(filename) -> None
pygame.mixier.music.play(loops=0, start=0.0)
pygame.mixier.music.pause()->None
pygame.mixier.music.stop() ->None
pygame.mixier.set_volume(value) ->None