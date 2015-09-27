![images](https://cloud.githubusercontent.com/assets/7239657/10121016/0831dc74-650b-11e5-84a4-1f0dceb88cd0.jpg)
# 序
* 当你默默撸代码的时候，是否想过让大家看到你卖力搬砖的过程
* 当你有一个团队的时候，是否想把团队的运作展示到项目主页上

# Webhook
要实现这样的功能并不难，现在的主流Git平台都提供了webhook接口，可以把git仓库操作事件推送到指定的服务器上。

## 常用Git平台（无需翻墙）
平台|托管|git事件支持|
------|-------|------------------------|
[github](https://developer.github.com/webhooks/)|公开项目免费，私有项目收费|所有
[oschina](http://git.oschina.net/)|免费|PUSH
[coding](https://coding.net/help/doc/git/webhook.html)|基础版本免费|Push/MR/PR/Topic/Task/Document/Watch/Star
[gitcafe](https://developer.gitcafe.com/#webhooks)|公开项目免费，私有项目收费|Push/Ticket/Pull Request/Ticket Comment/Pull Request Comment
[raindrop](http://www.yudianer.com)网当前支持接收github 和 oschina的`PUSH`事件
## 如何配置webhook
### Github配置
1. 打开项目设置
![image](https://cloud.githubusercontent.com/assets/7239657/10121140/858e961c-6510-11e5-9ba8-f78e05879e0b.png)
2. 选择左侧 `Webhooks & services`
3. 在 `Webhooks` 一栏点击 `Add webhook`
4. 填写关键信息
    * Payload URL：服务器接受推送事件的路由接口（例：如果使用[raindrop](http://www.yudianer.com)网来接受数据，配置为http://www.yudianer.com/api/github/webhook/你在raindrop网建立的项目名称）
    * Content type：服务器推送事件数据的类型，推荐使用application/json（[raindrop](http://www.yudianer.com)网当前接受的是json类型），比较容易处理。
    * Secret：用于服务器校验，防止恶意推送。
5. 选择需要推送的事件类型（[raindrop](http://www.yudianer.com)网当前支持手机PUSH事件）
6. 保存设置

### oschina配置
1. 打开项目主页
2. 打开项目管理页面
![image](https://cloud.githubusercontent.com/assets/7239657/10121273/95ccda2e-6516-11e5-9a8d-338dd01b215d.png  {width=40px height=40px})
3. 在左侧菜单栏选择`WebHook钩子`
4. 填写关键信息：
    * POST URL：服务器接受推送事件的路由接口（例：如果使用[raindrop](http://www.yudianer.com)网来接受数据，配置为http://www.yudianer.com/api/oschina/webhook/你在raindrop网建立的项目名称）
    * 密码：用于服务器校验，防止恶意推送。
5. 点击添加按钮。oschina可以把事件同时推送到多个服务器。

> 如果你将事件推送到了[raindrop](http://www.yudianer.com)网，当你每次提交数据后，都可以在项目主页中看到你的提交次数统计。（可以装b咯）

![image](https://cloud.githubusercontent.com/assets/7239657/10121201/828bb6ea-6513-11e5-9fc4-f7f3f66a8301.png)
