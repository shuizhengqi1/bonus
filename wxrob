# -*- coding:utf-8 -*-  
# 
# email =shuizhengqi1@163.com
# 
import  itchat
import requests
from itchat.content import *
import json
import time,threading
import sys
reload(sys)
sys.setdefaultencoding( "utf-8" )
@itchat.msg_register([TEXT])
def print_content(msg):
    return u'[自动回复]目前只支持分享链接到这里，然后去群里领取红包，等红包烹饪好了，会通知你的哦' \
           

@itchat.msg_register([SHARING])
def postTicket(msg):
    group = itchat.search_chatrooms(name=u'外卖红包直领群')
    header_dict = {'User-Agent': 'Mozilla/5.0 (Windows NT 6.1; Trident/7.0; rv:11.0) like Gecko',
                   "Content-Type": "application/json"}
    data = {'Title':msg['Text'],'shareUserName':msg['FromUserName'],'Url':msg['Url'],'Tid':msg['MsgId']}
    url = 'http://www.iotxing.org.cn/add'
    req = requests.post(url=url,data=data)
    return  req.content

@itchat.msg_register(FRIENDS)
def add_friend(msg):
    msg.user.verify()
    msg.user.send('hello')


itchat.auto_login(hotReload=True)
itchat.run()
