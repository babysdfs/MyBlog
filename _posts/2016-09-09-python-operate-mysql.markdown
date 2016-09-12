---
layout: post
title:  "python操作Mysql"
date:   2016-09-09 22:36:09 +0800
comments: [true]
categories: [python,mysql]
---
    #############################################################
    # -*- coding: utf-8 -*-
    def insert_database():
        conn=MySQLdb.connect(host='localhost',user='root',passwd='***',db='dbname',port=3306,unix_socket='/tmp/mysql.sock',charset='utf8')
        cursor=conn.cursor()  # 返回列表
        #cursor = conn.cursor(MySQLdb.cursors.DictCursor)   #返回字典，字典中的key为 mysql表中的字段
        table="test"
        #sql="insert into " + table + " (`uniquekey`,`aa`,`bb`,`date`) values(%s,%s,%s,%s);" 
        #sql="insert ignore into " + table + " (`uniquekey`,`aa`,`bb`,`date`) values(%s,%s,%s,%s);" # uniquekey已存在的话就不会插入那条数据
        sql="insert into " + table + " (`uniquekey`, `aa`, `bb`,`date`) VALUES (%s,%s,%s,%s) on duplicate key update `aa`=values(`aa`), `bb`=values(`bb`)"  # uniquekey是新的就正常插入,uniquekey已存在就强行update
        cursor.execute(sql,many)
        conn.commit()
        cursor.close()
        conn.close()
