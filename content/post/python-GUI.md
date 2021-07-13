+++
title = "Python GUI"
description = "Python GUI"
date = 2021-06-11
tags = ["Python"]
+++

今天來用Python內建的tkinter模組設計一個簡單的計算機

## 首先先引入會用到的模組

    import tkinter as tk
    from tkinter import *
    from tkinter.constants import  NSEW, RIGHT
    x = int

## 接著設定按鍵功能

    def math(x):
        if x == "exit":
            window.destroy()
        elif x in ["+", "-", "*", "/", "(", ")", "."] or x in map(str, range(0, 10)):
            if lab["text"] == "0":
                lab["text"] = x
            else:
                lab["text"] += x
        
        elif x == "=":
            lab["text"] = str(eval(lab["text"]))     #用eval函數將文字轉換成算式並返回計算結果
        
        elif x == "C":
            lab["text"] = "0"

## 設定視窗名稱、位置與大小

    window = tk.Tk()
    window.title("Label demo")
    window.geometry("500x600+100+50")

## 設定視窗排版

    window.rowconfigure(0,weight=1)
    window.rowconfigure(1,weight=1)
    window.rowconfigure(2,weight=1)
    window.rowconfigure(3,weight=1)
    window.rowconfigure(4,weight=1)
    window.rowconfigure(5,weight=1)

    window.columnconfigure(0,weight=1)
    window.columnconfigure(1,weight=1)
    window.columnconfigure(2,weight=1)
    window.columnconfigure(3,weight=1)

## 設定標籤與按鍵文字大小、字型和位置

    lab = Label(window, text="0", justify="right", anchor="e", font=("Calibri",26,"bold"))
    lab.grid(row=0,column=0, columnspan=4,sticky=NSEW)

    but = Button(window, text="9", font=("Calibri"), command=lambda:math("9"))
    but.grid(row=1, column=0, sticky=NSEW)

    but1 = Button(window, text="8", font=("Calibri"), command=lambda:math("8"))
    but1.grid(row=1, column=1, sticky=NSEW)

    but2 = Button(window, text="7", font=("Calibri"), command=lambda:math("7"))
    but2.grid(row=1, column=2, sticky=NSEW)

    but3 = Button(window, text="6", font=("Calibri"), command=lambda:math("6"))
    but3.grid(row=2, column=0, sticky=NSEW)

    but4 = Button(window, text="5", font=("Calibri"), command=lambda:math("5"))
    but4.grid(row=2, column=1, sticky=NSEW)

    but5 = Button(window, text="4", font=("Calibri"), command=lambda:math("4"))
    but5.grid(row=2, column=2, sticky=NSEW)

    but6 = Button(window, text="3", font=("Calibri"), command=lambda:math("3"))
    but6.grid(row=3, column=0, sticky=NSEW)

    but7 = Button(window, text="2", font=("Calibri"), command=lambda:math("2"))
    but7.grid(row=3, column=1, sticky=NSEW)

    but8 = Button(window, text="1", font=("Calibri"), command=lambda:math("1"))
    but8.grid(row=3, column=2, sticky=NSEW)

    but9 = Button(window, text="0", font=("Calibri"), command=lambda:math("0"))
    but9.grid(row=4, column=0, sticky=NSEW)

    but10 = Button(window, text="+", font=("Calibri"), command=lambda:math("+"))
    but10.grid(row=4, column=1, sticky=NSEW)

    but11 = Button(window, text="-", font=("Calibri"), command=lambda:math("-"))
    but11.grid(row=4, column=2, sticky=NSEW)

    but12 = Button(window, text="/", font=("Calibri"), command=lambda:math("/"))
    but12.grid(row=1, column=3, sticky=NSEW)

    but13 = Button(window, text="*", font=("Calibri"), command=lambda:math("*"))
    but13.grid(row=2, column=3, sticky=NSEW)

    but14 = Button(window, text="=", font=("Calibri"), command=lambda:math("="))
    but14.grid(row=3, column=3, sticky=NSEW)

    but15 = Button(window, text=".", font=("Calibri"), command=lambda:math("."))
    but15.grid(row=5, column=0, sticky=NSEW)

    but16 = Button(window, text="(", font=("Calibri"), command=lambda:math("("))
    but16.grid(row=5, column=1, sticky=NSEW)

    but17 = Button(window, text=")", font=("Calibri"), command=lambda:math(")"))
    but17.grid(row=5, column=2, sticky=NSEW)

    but18 = Button(window, text="C", font=("Calibri"), command=lambda:math("C"))
    but18.grid(row=4, column=3, sticky=NSEW)

    but19 = Button(window, text="exit", font=("Calibri"), command=lambda:math("exit"))
    but19.grid(row=5, column=3, sticky=NSEW)

    window.mainloop()

## 執行結果
![test](/GUI/test.jpg)

![test](/GUI/test1.jpg)

