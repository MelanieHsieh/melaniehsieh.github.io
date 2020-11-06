---
layout: post
title: "A replica of Amazon's Audible"
date: 2020-11-06 08:42:43 +0800
tags: code
comments: true
---

This month I've been playing around with machine learning and experimenting with different libraries. On the other hand, I've been wanting to read this new Chinese novel series, 慶餘年. It has 760 chapters, each chapter with a few thousand Chinese character. Also, this novel series was highly recommended by my cousin.

And this is what I came up...

An audiobook that is sort of a replica Amazon's Audible. Imagine there is a software where you paste in the link of the book, it converts the file into pdf then use text-to-speech recognition to read the characters out loud. How cool would that be...

Here the the 4 key steps:

# 1 Find the book online

I found this website that offers [慶餘年](http://big5.quanben-xiaoshuo.com/n/qingyunian/xiazai.html) in TXT format.

# 2 Convert TXT to PDF format

This took me a while as there were 760 chapters. But here is a simple snipet where I used the _pdfkit_ library to convert from txt to pdf.

```python
import pdfkit
import shutil

for i in site:
    title = i[14:-4] + '.pdf'
    pdfkit.from_url('http://big5.quanben-xiaoshuo.com' + i, title)

    old = r'' + title
    new = r'./慶餘年/' + title
    shutil.move(old,new)
```

# 3 Text to Speech

Here comes the fun part. I used Google's **gTTS Library** to process text into speech. They offer a wide range of language, including Cantonese, Mandarin, English, French etc. I then wrote a simple script to tell the program to read every character from the PDF document I generated previously.

However, the gTTS Library isn't the newest libary offered. It often skips past a few vocabulary such as **'⼦', '一', '黑'**. This made the whole audio book sounds incomplete making the whole user experience bad.

```python
from gtts import gTTS

myAudio = gTTS(text=output_string.getvalue(), lang='zh-yu', slow=False)

myAudio.save("Audio.mp3")
```

# 4 慶餘年 Chapter 1 Audiobook

<audio controls>
  <source src="/img/audiobook/Audio.mp3" type="audio/mp3">
</audio>
<!-- <embed height="100" width="auto" src="/img/audiobook/Audio.mp3"></embed> -->

### 慶餘年 Chapter 1 PDF snippet

楔⼦ ⼀塊⿊布
範慎很困難地撐著上眼⽪，看著指頭算⾃⼰這輩⼦做過些什麽有意義的事情，結果右⼿五根瘦成筷⼦⼀樣的指頭

還沒有數完，他就歎了⼀⼝氣，很傷⼼地放棄了這個⼯作。

病房裏的藥⽔味總是這麽刺⿐，旁邊那床的老爺⼦前兩天已經去地藏王菩薩那裏報道了，⼤概再過幾天就輪到⾃

他得了某種怪病，重症肌無⼒，就是特別適合男主⾓的那種病。據說沒得醫，將來嗝屁的那天什麽都動不了，隻

“可我不是⾔情啊。”範慎咕噥著，但由於兩頜的肌⾁沒有了作⽤，所以變成⼀串含糊的囈語。

他望著⾃⼰的中指頭，很同情⾃⼰，“我還是處男。”

⼰吧。

有眼淚可以流下來。

### Nung Update

Nung is still in progress, was a bit behind the schedule as I haven't test it on a Parkinson's Disease patient. Will be coming soon shortly...

If you have any further question you can always email me at <mpwh2004@gmail.com> or find me on [Github](https://github.com/melaniehsieh).

Please subscibe to my monthly blog to get the latest updates.

Thanks for reading 👀. There will be a monthly blog every month on the first week of Friday, Stay Tuned.😉
