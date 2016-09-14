---
layout: post
title:  "python的urllib2库"
date:   2016-09-09 22:36:09 +0800
comments: [true]
categories: [python,urllib2]
---
http://dillinger.io/    markdown在线编辑    

    ########## urllib2 传入 header 以get的方式访问url #############
    import urllib2
        url='http://api.byfen.com/app/down_web/125139'
        headers={
        "Accept":"text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8",
        "Accept-Encoding":"gzip, deflate, sdch",
        "Accept-Language":"zh-CN,zh;q=0.8",
        "Connection":"keep-alive",
        "Cookie":"web_byfen=e623c220e6d10d35e0c40a7405290c5e02cf17eb%2BARwMuxSewmhw3IJ22OZ9yHJiw5   GNaa60SfYPTUK8",
        "Referer":"http://android.byfen.com/app/12661",
        "Upgrade-Insecure-Requests":1,
        "User-Agent":"Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/52.0.2743.116 Safari/537.36"
        }
        req = urllib2.Request(url)
        for k,v in headers.iteritems():   #传入headers
             req.add_header(k,v)
        response=urllib2.urlopen(req)
        print response.headers  #返回的header
        print response.__dict__.keys()
        print response.read()   #返回的body
