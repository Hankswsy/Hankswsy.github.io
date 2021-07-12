+++
title = "Python Class"
description = "Python Module"
date = 2021-03-12
tags = ["Python"]
+++

今天來記錄一下這個簡單的Python "物件"寫法

    class Commander:      #建立一個Commander類別(Class)
        '''               #描述這個類別(Class)
        --------------------------------------------
        象棋 
        1.名稱 2.代號 3.顏色 4.位階 5.可移動方式
        --------------------------------------------
        '''
        def __init__(self, name, id, atk, hp, sp):  #建構式(Constructor)
            self.comName = name
            self.comId = id
            self.comAtk = atk
            self.comHp = hp
            self.comSp = sp 

        def showinfo(self):                 #方法(Method)
            print("1.",self.comName)
            print("2.",self.comId)
            print("3.",self.comAtk)
            print("4.",self.comHp)
            print("5.",self.comSp)

    #建立Commander類別(Class)的物件(Object)
    x = Commander("將","1","黑","王","執行一步")
    y = Commander("士","2","紅","保護王","執行一步")
    z = Commander("卒","3","黑","直行","執行一步")

    print(Commander.__doc__)
    x.showinfo()
    print("--------------------------------------")
    y.showinfo()
    print("--------------------------------------")
    z.showinfo()

執行結果
![test](/Class/test.jpg)