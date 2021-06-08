+++
title = "Python 照片特效處理"
description = "Python photo effects processing"
date = 2021-06-04
tags = ["Python"]
+++

今天來記錄一下最近學到的有趣Python應用照片特效處理。
主要使用PIL模組裡的功能

## 首先先引入模組
    from PIL import Image          
    from PIL import ImageFilter

Image 主要處理改變照片格式、大小等功能

ImageFilter 可以將照片套用不同的濾鏡

## 開啟照片
    img1 = Image.open("test.jpg")
這是用來測試的照片
![eraser](/photo-effects(python)/test.jpg)

## 1. 讓照片清晰
    img2 = img1.filter(ImageFilter.DETAIL)
    img2.save("DETAIL.jpg")
![eraser](/photo-effects(python)/DETAIL.jpg)

## 2. 畫出照片輪廓
    img3 = img1.filter(ImageFilter.CONTOUR)
    img3.save("CONTOUR.jpg")
![eraser](/photo-effects(python)/CONTOUR.jpg)

## 3. 讓照片模糊
    img4 = img1.filter(ImageFilter.BLUR)
    img4.save("BLUR.jpg")
![eraser](/photo-effects(python)/BLUR.jpg)

## 4. 尋找邊緣
    img5 = img1.filter(ImageFilter.FIND_EDGES)
    img5.save("FIND_EDGES.jpg")
![eraser](/photo-effects(python)/FIND_EDGES.jpg)

## 5. 邊緣增強
    img6 = img1.filter(ImageFilter.EDGE_ENHANCE)
    img6.save("EDGE_ENHANCE.jpg")
![eraser](/photo-effects(python)/EDGE_ENHANCE.jpg)
    
## 6. 邊緣增強更多
    img7 = img1.filter(ImageFilter.EDGE_ENHANCE_MORE)
    img7.save("EDGE_ENHANCE_MORE.jpg")
![eraser](/photo-effects(python)/EDGE_ENHANCE_MORE.jpg)

## 7. 浮雕效果
    img8 = img1.filter(ImageFilter.EMBOSS)
    img8.save("EMBOSS.jpg")
![eraser](/photo-effects(python)/EMBOSS.jpg)

## 8. 光滑效果
    img9 = img1.filter(ImageFilter.SMOOTH)
    img9.save("SMOOTH.jpg")
![eraser](/photo-effects(python)/SMOOTH.jpg)

## 10. 銳化
    img10 = img1.filter(ImageFilter.SHARPEN)
    img10.save("SHARPEN.jpg")
![eraser](/photo-effects(python)/SHARPEN.jpg)

