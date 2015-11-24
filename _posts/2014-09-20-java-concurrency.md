---
layout: post
title: ios push model注意事项
category: iOS技术
comments: true
---
##如果一个视图只需导到另一个视图，不需要返回，则使用model.如果用了导航，则使用push.
##在自定义cell中不建议使用cell拖动segue，一般还是用视图拖动到另一个视图的segue。
##通过点击cell数据传递给下一个视图:didselected方法中使用[self performsegueidtifier with sender].然后在方法prepareforsegue中添加数据sender
