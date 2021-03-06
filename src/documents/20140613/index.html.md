---
title: "最近解决了一个比较复杂的“死锁”问题"
layout: "note"
link: http://stackoverflow.com/questions/24054940/wpf-application-hang-by-propertychangedeventmanager-in-concurrent-environments/24203518#24203518
note_date: "2014-06-13"
---

前段时间公司里的程序在极少的情况下会出现“死锁”问题。其实也不能算是“前段时间”，因为这个问题时不时会出现一次，持续了一年多了吧，但由于出现次数很少，所以也一直没有动力去挖出原因来。最近由于系统变得越来越复杂，使用者也越来越多，出现的频率上升到一周一两次，于是我们也就下决心把它解决掉。

但是这个问题实在有些麻烦，它看上去像是死锁，但却无法在内存中找到“锁”的痕迹。最后阻塞的代码是在获取“读写锁”中的“读锁”，但此时的“写锁”也在当前线程手中，因此理应可以正确访问。

我在StackOverflow上详细地描述了这个问题，也在MVP内部邮件列表里抄送了一份，但始终没有得到有价值的回复。有意思的是，InfoQ首席.NET编辑Jonathan Allen也回答了这个问题，说的很简单，但没答在点上，而且我并不同意他的看法……

我现在在想，其实StackOverflow是否适合稍微复杂一些的问题，因为这样的问题往往需要深入分析，甚至需要来回补充更多资料，但大家都很忙，对于此类问题甚至没有精力去读完它的描述。而且高手的时间都很宝贵，放在我身上也不会愿意花三个小时去解决别人的问题，我是要卖每小时1000块钱的呢。

最后我还是自己解决了这个问题，为此我几乎看遍了所有相关方法的内部实现。我把问题的原因和解决方案详细地写在了那个问题后面，还挺花了一番功夫。还好我从来不怕把一个问题讲清楚，多少年博客写下来，早就充分锻炼了表达能力。

其实这也是我在工作中经常做的事情。除了开发，我经常要想办法解决系统中的疑难杂症。我的老板有着深厚的技术背景，几乎没法糊弄过去，每个问题都要解释清楚才行，因此这种大段的分析文字也经历过不知道多少次。

点击“<span style="color:blue;">阅读原文</span>”可以跳转至该问题及其答案。建议您耐心阅读，要知道深入分析并解决一个问题是十分有益处的练习。最后假如您觉得有所帮助，也不妨在StackOverflow上给我点个赞，谢谢。