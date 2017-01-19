# DZMeBookRead

Epub的同学请看这里: 用WebView来做 那需要JS功底而且效果还没那么好, 那么可以参考这个大神的思路把它解析成跟Txt一样的章节文件进行阅读:https://github.com/GGGHub/Reader, 可以只看他的Epub解析代码即可,获得章节字符串之后跟我的Demo一样都转成章节模型存起来 就都是一样了, 封面图片什么都是可以进行图文混排的。 你要是JS好的话可以忽略这句话, 我只提供思路不做SDK


本次更新 : 

已更新Swift3.0 Xcode版本: Xcode8.1 该Demo仅供参考思路（重点思路: 阅读效果 以及 切换阅读效果 思路）

1.上下滚动的内存问题 现在只要看不见的章节都会进行清理内存 不会占用内存

2.修改了一个BUG  上下滚动模式中 左侧滑栏切换章节之后 往上滚会快速切换章节问题 已修复

重要BUG: 上下滚动之后 切换字体 往上滚动 由于字体变化 那么cell的高度也会变化 这个时候滚动上去显示新的章节 会造成tableview 上移或者下推问题 这个也是上下滚动模式最麻烦的BUG 已修复

原作者DZM 最完整小说阅读器Demo 

翻页效果(无效果,覆盖,仿真,上下滚动) 

时间 电池(有单独封装 使用2行代码即可支持电池 电池支持黑白模式) 章节尾部占位广告图片(可取消) 

支持字体 字体大小切换 背景颜色切换 书签功能 等等.. 

阅读记录保存与下次阅读定位 亮度调整 

Txt格式解析（由于存放字体文件会导致文件太大 我这里面的字体就随便用了几个系统的代替下 这样下载包也小,由于先写完公司项目则文件名用的是公司前缀没时间改将就啦) 

小说《覆盖效果》DZMCoverAnimation: https://github.com/dengzemiao/DZMCoverAnimation


                                                                            ---------------- 技术QQ群:52181885

#Demo效果GIF：

![CarouselView in action](Untitled.gif)

#书签使用效果GIF：

![CarouselView in action](bookMark.gif)

#项目思路：

通过一个txt文件解析成 无数个章节模型(也可以理解成无数个 章节.txt文件) 这些章节模型文件使用归档进行存储起来 (可以运行项目之后进入沙河路径看看我的文件夹结构就明白了) 

然后在阅读中每次通过一个章节ID 就能快速获取以及解析出来一个章节模型 进行使用 不用了直接进行销毁 保证了内存问题
在下载章节缓存小说方面 也是有利的 阅读的整个过程中面对的只有章节ID 通过章节ID就能知道这个章节是否存在以及能够拿出来解析阅读 同时还可以在后台在任何地方进行下载缓存 而不会出问题 因为你只需要去通过章节ID 去获取章节model归档文件即可

同样 既然章节模型都有了归档 也需要一个正对整本书的 缓存 章节信息 书本信息 阅读记录 等等的BOOK模型 这个模型也使用归档进行存储 在重新进入阅读的时候 归档秒解析的速度能够无视觉的延迟的快速进入 然后获取阅读记录进行定位阅读 当然这样也是可以通过网络数据进行更新的

以上的思路针对本地 网络数据都是可行的
