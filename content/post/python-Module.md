+++
title = "Python Module"
description = "Python Module"
date = 2021-03-05
tags = ["Python"]
+++

今天來記錄一下這個簡單的Python 模組應用
如果程式中需要反覆使用同一段程式碼的話，將它寫成模組是不錯的選擇。

首先先建立一個簡單的程式

    import sys       #先引入sys模組他能直接讀取命令

    import mod       #引入自己寫的模組，名稱是要引入的檔案名稱，我以mod為例

    if sys.argv[1]=="fun1":#亂數選號
    print(mod.fun1(sys.argv[2:7]))

    elif sys.argv[1]=="fun2":#C(m,n) 
        x=int(sys.argv[2])
        y=int(sys.argv[3])
        print(mod.fun2(x,y))

    elif sys.argv[1]=="fun3":#數字排序
        y=int(sys.argv[2])
        print(mod.fun3(sys.argv[3:y+3]))
        
    elif sys.argv[1]=="fun4":#list元素平方
        y=len(sys.argv)
        print(mod.fun4(sys.argv[2:y]))

    elif sys.argv[1]=="fun5":#連續元素和為0
        x=int(sys.argv[2])
        print(mod.fun5(sys.argv[3:x+3]))

接下來開新的一個py檔，放入要執行的程式

    import random

    def fun1(x):          #亂數選擇
        return random.choice(x)

    def fun2(x,y):        #C(m,n)
        a=1
        b=1
        c=1
        for i in range(1,x+1):
            a=a*i
        for j in range(1,y+1):
            b=b*j
        for k in range(1,(x-y)+1):
            c=c*k
        return a//(b*c)

    def fun3(x):         #數字排序
        a=[]
        for i in range(len(x)):
            a.append(int(x[i]))
        for k in range(len(a)-1,-1,-1):
            for j in range(k):
                if a[j]>a[j+1]:
                    z=a[j]
                    a[j]=a[j+1]
                    a[j+1]=z     

        return a

    def fun4(y):        #list元素平方
        x=[]
        for i in range(len(y)):
            x.append(int(y[i]))
        for i in range(len(x)):
            x[i]=x[i]**2
        return x

    def fun5(x):        #連續元素和為0
        a=0
        y=[]
        for i in range(len(x)):
            y.append(int(x[i]))
        for j in range(len(y)-2):
            a=y[j]+y[j+1]+y[j+2]
            if a==0:
                return y[j],y[j+1],y[j+2]

最後執行結果如下

我寫的第一個function是在一堆數字中隨機選號
![test](/module/test.jpg)

我寫的第二個function是數學中的排列組合
![test](/module/test1.jpg)

我寫的第三個function是數字排序
![test](/module/test2.jpg)

我寫的第四個function是將list元素平方
![test](/module/test3.jpg)

我寫的第五個function是檢查哪幾個元素相加為0
![test](/module/test4.jpg)
        