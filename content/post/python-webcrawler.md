+++
title = "Python Webcrawler"
description = "Python Webcrawler"
date = 2021-04-12
tags = ["Python"]
+++

今天來記錄一下Python爬蟲
python爬蟲是一門說簡單也不簡單，說困難也不困難的應用
透過撰寫Python爬蟲技術，可以省下以往要一筆一筆資料手動抓取的時間，並且可以精準的拿到資料

範例是以[majortests](https://www.majortests.com/)這個網站裡提供的Word List做示範

## 首先先引入爬蟲需要的mod

    import requests
    from bs4 import BeautifulSoup as bs
    import time
    import csv

## 接著設定目標的網址

    url = "https://www.majortests.com/word-lists/word-list-{}.html"
    #"{}"是要放入不同頁面編號的地方

## 用for迴圈設定要取得那些頁面

    def num(url, start, end):
        urll = []
        x = str
        for i in range(start, end+1):
            x="{:02d}".format(i)
            urll.append(url.format(x))
        
        return urll

## 伺服器驗證

    def get_resource(url):
        headers = {"user-agent":"Mozilla/5.0(Windows NT 10.0; Win64; x64) ApplWebKit/537.36 (KHTML, like Gecko) Chrome/63.0.329.130 Safari/537.36"}
        return requests.get(url, headers=headers)

## 取得網頁HTML

    def catchingwordbot(urls):
        eng_words=[]
        for i in urls:
            file = i.split("/")[-1]
            print("catching: ", file, "web data...")
            r = get_resource(i)
            if r.status_code == requests.codes.ok:
                soup = webcode(r.text)
                words = get_word(soup, file)  
                eng_words = eng_words + words
                print("wait 5 sec")
                time.sleep(5)  #避免被判定是DDoS攻擊，以每5秒請求一次
            else:
                print("http request error!")

        return eng_words

## 解析回傳的HTML

    def webcode(r):
        return bs(r, "html.parser")

## 分析HTML並提取出目標

    def get_word(soup,file):
        word = []
        count = 0
        for data in soup.findAll(class_="wordlist"):
            count += 1
            for word_e in data.findAll("tr"):
                new_word = []
                new_word.append(file)
                new_word.append(f"Grop{str(count)}")
                new_word.append(word_e.th.text)
                new_word.append(word_e.td.text)
                word.append(new_word)
        return word

## 將目標整理成csv檔

    def excelsave(word,name):
        with open(f'{name}.csv', 'w', newline='', encoding="UTF8") as csvfile:
            
            writer = csv.writer(csvfile)
            for i in word:
                # 寫入一列資料
                writer.writerow(i)

## 主程式

    if __name__ == "__main__":
        x="EnglishWord"
        urls = num(url, 1, 10)
        eng_words = catchingwordbot(urls)
        excelsave(eng_words,x)


## 執行結果
![test](/webcrawler/test.jpg)

## CSV檔
![test](/webcrawler/test1.jpg)

## 完整程式碼

    import requests
    from bs4 import BeautifulSoup as bs
    import time
    import csv

    url = "https://www.majortests.com/word-lists/word-list-{}.html"

    def num(url, start, end):
        urll = []
        x = str
        for i in range(start, end+1):
            x="{:02d}".format(i)
            urll.append(url.format(x))
        
        return urll

    def get_resource(url):
        headers = {"user-agent":"Mozilla/5.0(Windows NT 10.0; Win64; x64) ApplWebKit/537.36 (KHTML, like Gecko) Chrome/63.0.329.130 Safari/537.36"}
        return requests.get(url, headers=headers)

    def webcode(r):
        return bs(r, "html.parser")

    def get_word(soup,file):
        word = []
        count = 0
        for data in soup.findAll(class_="wordlist"):
            count += 1
            for word_e in data.findAll("tr"):
                new_word = []
                new_word.append(file)
                new_word.append(f"Grop{str(count)}")
                new_word.append(word_e.th.text)
                new_word.append(word_e.td.text)
                word.append(new_word)
        return word

    def catchingwordbot(urls):
        eng_words=[]
        for i in urls:
            file = i.split("/")[-1]
            print("catching: ", file, "web data...")
            r = get_resource(i)
            if r.status_code == requests.codes.ok:
                soup = webcode(r.text)
                words = get_word(soup, file)  
                eng_words = eng_words + words
                print("wait 5 sec")
                time.sleep(5)
            else:
                print("http request error!")

        return eng_words

    def excelsave(word,name):
        with open(f'{name}.csv', 'w', newline='', encoding="UTF8") as csvfile:
            
            writer = csv.writer(csvfile)
            for i in word:
                # 寫入一列資料
                writer.writerow(i)


    if __name__ == "__main__":
        x="EnglishWord"
        urls = num(url, 1, 10)
        eng_words = catchingwordbot(urls)
        excelsave(eng_words,x)