# The-Fighting-of-Planes
一个使用C#开发的模仿微信飞机大战游戏Demo

**总体设计思路**

（1）万物皆对象

　　在整个游戏中，我们看到的所有内容，我们都可以理解为游戏对象（GameObject），每一个游戏对象，都由一个单独的类来创建；在游戏中主要有三类游戏对象：一是飞机，二是子弹，三是背景；其中，飞机又分为玩家飞机和电脑飞机，子弹又分为玩家子弹和电脑子弹。于是，我们可以对飞机进行抽象形成一个抽象父类：PlaneBase，然后分别创建两个子类：PlanePlayer和PlaneEnemy；然后对子弹进行抽象形成一个抽象类：BulletBase，然后分别创建两个子类：BulletPlayer和BulletEnemy。但是，我们发现这些游戏对象都有一些共同的属性和方法，例如X，Y轴坐标，长度和宽度，以及绘制（Draw()）和移动（Move()）的方法，这时我们可以设计一个抽象类，形成了GameObject类：将共有的东西封装起来，减少开发时的冗余代码，提高程序的可扩展性，符合面向对象设计的思路：

![markdown](https://images0.cnblogs.com/blog/381412/201501/252045152693854.jpg "markdown")
![markdown](https://images0.cnblogs.com/blog/381412/201501/252044084419603.jpg "markdown")

（2）计划生育好

　　在整个游戏中，我们的玩家飞机对象只有一个，也就是说在内存中只需要存一份即可。这时，我们想到了伟大的计划生育政策，于是我们想到了使用单例模式。借助单例模式，可以保证只生成一个玩家飞机的实例，即为程序提供一个全局访问点，避免重复创建浪费不必要的内存。当然，除了玩家飞机外，我们的电脑飞机集合、子弹集合等集合对象实例也保证只有一份存储，降低游戏开销；

（3）对象的运动

　　在整个游戏过程中，玩家可以通过键盘上下左右键控制玩家飞机的上下左右运动，而飞机的运动本质上还是改变游戏对象的X轴和Y轴的坐标，然后一直不间断地在窗体上重绘游戏对象。相比玩家飞机的移动，电脑飞机的移动则完全是通过程序中设置的随机函数控制左右方向移动的，而玩家飞机发出的子弹执行的运动则是从下到上，而电脑飞机发出的子弹执行的运动则是从上到下。

![markdown](https://images0.cnblogs.com/blog/381412/201411/221526463128324.png "markdown")

（4）设计流程图

![markdown](https://images0.cnblogs.com/blog/381412/201501/252210498478130.png "markdown")

## 效果演示

*主要分为游戏端和服务端*

### 服务端开起服务

![Pandao editor.md](https://images0.cnblogs.com/blog/381412/201501/252224181596573.jpg "Pandao editor.md")

服务器端主要开启监听玩家连接请求的服务，当几个处在同一局域网的玩家连接后，服务端管理员点击“开始游戏”则客户端会启动游戏。

### 服务端开起服务

![Pandao editor.md](https://images0.cnblogs.com/blog/381412/201501/252226295349942.jpg "Pandao editor.md")
在客户端中，玩家飞机可以通过不停地发射子弹向不同类型的电脑飞机来获取得分，但是如果被敌人飞机的子弹击中分数也会被扣去一部分。

### 服务端计算成绩客户端显示
![Pandao editor.md](https://images0.cnblogs.com/blog/381412/201501/252230193313013.jpg "Pandao editor.md")
![Pandao editor.md](https://images0.cnblogs.com/blog/381412/201501/252230300508822.jpg "Pandao editor.md")

> 当两个玩家连接游戏服务端后，便开始了“打飞机”的战斗，当指定时间后游戏结束，显示各自的游戏名次和分数。

　　当然，还有很多核心的内容没有实现。希望有兴趣的童鞋可以去继续完善实现，这里提供一个我的飞机大战实现仅供参考，谢谢！

### 参考博文

URL：<http://www.cnblogs.com/edisonchou/p/4248783.html>

> @EdisonChou

