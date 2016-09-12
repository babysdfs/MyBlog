---
layout: post
title:  "python操作Mysql"
date:   2016-09-09 22:36:09 +0800
comments: [true]
categories: [python,mysql]
---
#############################################################
    conn=MySQLdb.connect(host='localhost',user='root',passwd='***',db='dbname',port=3306,unix_socket='/tmp/mysql.sock',charset='utf8')
    cursor=conn.cursor()  # 返回列表
    #cursor = conn.cursor(MySQLdb.cursors.DictCursor)   #返回字典，字典中的key为 mysql表中的字段
    sql="set global max_allowed_packet=33554432" #so we can drop the data up to 30m into database in a single time
    cursor.execute(sql)
    conn.commit()
    cursor.close()
    conn.close()
