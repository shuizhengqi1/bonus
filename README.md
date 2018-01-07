## 业务流程图

![红包电饭锅](https://ceshi-1255768919.cos.ap-chengdu.myqcloud.com/1b694658d65d66aee3ea0fec15b716f0.jpeg)



### 数据库要求

## ticketJob

| 列名         | 类型       | 备注                 |
| ---------- | -------- | ------------------ |
| title      | char     | 红包标题               |
| url        | text     | 红包链接               |
| bonus      | int      | 大红包所在位置            |
| username   | char     | 发包人的username       |
| company    | char     | 红包所属的公司            |
| tid        | char     | 微信的消息id，可作为唯一标示    |
| limit      | char     | 红包类型，是只能自己领还是可以别人领 |
| createtime | datetime | 创建时间               |
|            |          |                    |

## ticketUser

| 列名      | 类型   | 描述                                   |
| ------- | ---- | ------------------------------------ |
| userid  | char | 用户标识，微信公众号或者小程序能够获取到，web可以用cookie来代替 |
| company | char | 公司                                   |
| url     | text | 红包链接                                 |

## ticketUrl

| 列名         | 类型       | 描述          |
| ---------- | -------- | ----------- |
| userName   | char     | 用户的userName |
| createtime | datetime | 创建时间        |
| url        | text     | 红包链接        |

## ticketNotiQuene

| 列名       | 类型   | 描述     |
| -------- | ---- | ------ |
| userName | char | 用户名    |
| url      | text | 红包链接   |
| tid      | char | 微信消息id |



### 能够实现的功能

1. 用户转发红包到红包机器人，然后机器人可以发红包给服务器
2. 一个用户可以发两个可以自领的红包，这两个红包别人领不了，如果用户的发包数量超过两个，则任何人都能够领取大红包，而且也不会通知用户
3. 每个人每天每个公司最多能够领4个别人发的红包，总共八个，因为考虑到每个人自己还会发一个，所以一个是可以领五个
4. 机器人定时循环获取notiquene列表，然后根据username给用户发送领取红包的通知
5. 已经发布出来的红包不能够重复发送

### 存在的缺陷

1. 统计不准确，如果用户乱点或者一个红包到处发，可能会导致计数出错
2. 微信机器人容易被封

