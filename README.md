長庚大學 大數據分析方法 作業三
================

網站資料爬取
------------

``` r
##install.packages("rvest") ##安裝
library(rvest) ##載入
```

    ## Loading required package: xml2

``` r
dataframeAll=NULL
for(i in 5289:5299){
url=paste0("http://www.ptt.cc/bbs/movie/index",i,".html",sep='')
PTT_Title = read_html(url) %>% html_nodes(".title") %>% html_text()
PTT_PushNum = read_html(url) %>% html_nodes(".nrec") %>% html_text()
PTT_Author = read_html(url) %>% html_nodes(".author") %>% html_text()
dataframe = data.frame(title = PTT_Title, PushNum=PTT_PushNum, Author=PTT_Author)
dataframeAll<-rbind(dataframeAll,dataframe)
}
```

爬蟲結果呈現
------------

``` r
knitr::kable(
    dataframeAll[1:120,c("title","PushNum","Author")])
```

| title                                               | PushNum | Author       |
|:----------------------------------------------------|:--------|:-------------|
| \[好雷\] 聲之形                                     | 1       | andrew0621   |
| (本文已被刪除) <j210749133>                         | 33      | -            |
| \[討論\] 美女與野獸的一些問題                       | 14      | rrouyyin     |
| \[贈票\] 麥可法斯賓達【犯罪教條】PTT推文看電影      | 爆      | kkaicd1      |
| \[負雷\]本能寺大飯店--真的這麼好看嗎                | 10      | jkuhih       |
| (本文已被刪除) <Eddward>                            | 33      | -            |
| \[超大雷\] 有關目擊者的一個疑問                     | 19      | harry7319    |
| \[討論\] 爛番茄百大電影 2017/3月版                  | 13      | peter220     |
| \[好雷\] 目擊者 看完後幾個雜(猜)想                  | 17      | oaboy        |
| \[請益\] 美國隊長兩個問題                           | 14      | StarLeauge   |
| \[討論\] War Machine                                | 2       | yylin3266    |
| \[好雷\] 目擊者                                     | 4       | engineer1    |
| \[好雷\] 攻殼機動隊(2017) 新舊影迷皆可欣賞          | 18      | Scutum       |
| \[好雷\] 目擊者                                     | 3       | yesport      |
| \[請益\] 美女與野獸imax版畫面模糊？                 | 18      | chyilian     |
| \[討論\] 四海好傢伙的Ray Liotta為什麼沒紅？         | 7       | ADIMM        |
| \[討論\] 誰能告訴我荒島驚魂在演什麼...              |         | laiyuhao     |
| \[普雷\] 攻殼機動隊，記憶會害人                     | 1       | samuel60303  |
| \[討論\] 推薦Hans zimmer風格配樂的電影              | 19      | nurais1127   |
| \[無雷\] 聲之形 小失望                              | 9       | riceberg     |
| \[請益\] 目擊者有血腥畫面嗎？                       | 13      | jarryjarry   |
| \[普雷\] 目擊者 台灣版羅生門                        | 14      | kickyourface |
| \[普雷\] 逃出絕命鎮get out                          | 3       | klaikick     |
| \[新聞\] 電影台小編亂畫挨嗆 眾小編暴動給拍拍        |         | sampsonlu919 |
| \[新聞\] 張國榮7變身幻化程蝶衣　唐唐眷戀癡守愛      | 10      | huanglove    |
| Re: \[請益\] 美國隊長兩個問題                       | 6       | KingKingCold |
| \[新聞\] 《逃出絕命鎮》評價大好！喬登皮爾成《       | 2       | linkcat      |
| \[新聞\] Riot創始人瑞茲：想將英雄聯盟搬上銀幕       | 27      | zkow         |
| \[普雷\] 攻殼機動隊IMAX 3D                          | 6       | kaleo        |
| \[新聞\] 最佳男主角候選人注意！丹尼爾戴路易斯主     | 23      | DantesChen   |
| \[片單\] 歐美恐怖片（鬼沒有直接現身的)              | 11      | jacktakuya   |
| \[請益\] 決戰異世界中背景一問                       | 5       | azlbf        |
| \[討論\] 布萊德彼特無緣《死侍2》Cable一角           | 10      | jay5566      |
| \[普好雷\]《我的叔叔》，廢柴叔叔的生活哲學。        | 3       | a122239      |
| \[問片\] 韓國 師生片 卸屍宴 已解決                  | 2       | onlyjh       |
| \[片單\] 愚人節應景電影<sub>~</sub>                 | 59      | museangel    |
| Fw: \[新聞\] AlphaGo人機大戰電影紀錄片4月將全球首映 | 6       | zkow         |
| \[討論\] 蜘蛛人未來將退出漫威電影宇宙？             | 5       | jay5566      |
| \[問片\] 一部8、90年代，鎮上一堆吸血鬼的電影(解決)  | 2       | x77          |
| \[評論\] 聞天祥談 / 傳奇女星李麗華（1924-2017）     | 9       | MyAll        |
| \[新聞\] 《環太平洋2》正式殺青！！！！！！！        | 42      | jay5566      |
| (本文已被刪除) <AceRocker>                          | 7       | -            |
| \[有雷\] 教育的抉擇《神奇大隊長》                   |         | KevinMoleaf  |
| \[新聞\] 金馬好評 國寶音效師的工作紀實《擬音》      | 4       | MyAll        |
| \[ 雷\] 重案對決的問題                              | 1       | jeanskin420  |
| \[討論\] 玩命關頭紅在哪                             | 58      | j408723      |
| \[好雷\] 波麗娜 Polina, danser sa vie               | 5       | mysmalllamb  |
| \[普雷\] 國片 目擊者 簡單小評                       | 14      | lady012266   |
| \[業障雷\]廢墟花園與空殼虎鶇《攻殼機動隊》(上       | 19      | lightlucky   |
| \[討論\] 金城武 & 周冬雨《喜歡你》預告              | 4       | qpr322       |
| \[負雷\]點評《停屍姦》//爆雷                        | 5       | KACIRIE      |
| \[好雷\] 點評《危機救援》：血脈噴張空難鉅作         |         | KACIRIE      |
| Re: \[討論\] 玩命關頭紅在哪                         | 3       | StarLeauge   |
| Re: \[討論\] 玩命關頭紅在哪                         | 23      | neverlight   |
| \[普雷\] AI人工智慧                                 | 6       | uland26922   |
| \[選片\] 寵物情劫vs冠軍女兒                         | 7       | soome        |
| \[新聞\]「黑寡婦」史嘉蕾預告將退演藝圈　受訪        | 5       | gmuguruza    |
| \[好雷\] 攻殼機動隊2017-充滿視覺震撼                | 18      | ck0413       |
| \[普雷\] 一念無明 - 誠意十足，能力不足              |         | flowergone   |
| Re: \[討論\] 玩命關頭紅在哪                         | 30      | bilinear     |
| 〔負無雷〕寶貝老闆                                  | 17      | claire8      |
| \[討論\] 目擊者                                     | 5       | howpa        |
| \[新聞\] 雷利史考特透露《普羅米修斯》如何(有雷)     | 9       | Wall62       |
| \[普雷\] 點評【她其實沒那麼壞】//爆雷               | 2       | KACIRIE      |
| Re: \[新聞\] 雷利史考特透露《普羅米修斯》如何(有雷) | 5       | killua92     |
| \[請益\] 卸屍宴的人怎麼死的?                        | 2       | jazy6804     |
| \[討論\] 讓你人生第一次看到回家睡不著覺的電影       | 爆      | XDGEE        |
| \[普雷\] 特效令人驚豔的攻殼                         | 5       | DDD          |
| \[好雷\] 目擊者                                     | 5       | ktl          |
| \[評論\] 中國首週票房僅 350 萬 八月如何拿下金馬     | 16      | MyAll        |
| \[新聞\] 新片看板 目擊者迎戰攻殼機動隊              | 26      | iam168888888 |
| \[開箱\] 本能寺大飯店 原聲CD                        | 1       | chinaeatshit |
| \[LIVE\] 與森林共舞 東洋片首播21:00                 | 12      | pttnowash    |
| \[Live\] Hollywood 21:00 帝國戰神：巴霍巴利王       | 38      | lowes        |
| \[新聞\] 白人演亞洲人 好萊塢演員頻"洗白"惹議        | 15      | y91yi39      |
| \[討論\] 有人看過 Here Alone 這部電影嗎?(有雷)      |         | kahlo        |
| \[問片\] 公司中躲藏                                 | 4       | KDlove       |
| \[好雷\] 聲之形劇場版(補充原作版內容)               | 14      | jpd          |
| (本文已被刪除) \[njjack\]                           |         | -            |
| \[討論\] 關於目擊者                                 | 7       | nk930043     |
| \[普雷\] 我和我的冠軍女兒                           | 17      | redcard      |
| \[負雷\] 攻殼機動隊2017：有皮無肉，有肉無骨         | 17      | a80568911    |
| (本文已被刪除) <Eileen1116>                         | 51      | -            |
| \[好雷\] 攻殼機動隊                                 | 13      | Mahoutsukai  |
| \[普雷\] 點評《為了與你相遇》微雷                   | 3       | KACIRIE      |
| \[蠻好雷\]目擊者                                    | 15      | sazanami726  |
| \[普負雷\]攻殼機動隊-攻殼迷純吐嘈                   | 27      | joyca        |
| \[討論\] 目擊者上映幾天啊.....                      | X3      | hayuyang     |
| \[問片\] 某部西洋愛情片關於靈魂出竅                 | 1       | CoffeeBe     |
| \[好雷\] 《青春倒退嚕》如實接受自己                 | 3       | cybeth       |
| \[負雷\] 2017年攻殼機動隊腦粉心得以及暴雷           | 17      | efairy       |
| \[普雷\] 攻殼機動隊                                 | 3       | mikemagic88  |
| \[新聞\] 謝婷婷認愛鷹眼！進展神速「已見過家長」     | 55      | peter080845  |
| Re: \[新聞\] 白人演亞洲人 好萊塢演員頻"洗白"惹議    | 9       | ivorysoap    |
| \[好雷\] 目擊者                                     | 9       | ya911019     |
| \[情報\] 《亞瑟：王者之劍》終極官方預告拔起         | 32      | SKnight      |
| \[好雷\] 魅惑人魚姬                                 | 3       | lovelydaisy  |
| \[討論\] 目擊者(有雷)                               | 7       | itis0423     |
| \[負雷\] 攻殼機動隊                                 | 2       | WalterWhite  |
| \[惆悵好雷\] 明天，我要和昨天的妳約會 太惆悵了      | 8       | max6060789   |
| \[普雷\] 點評《漫漫回家路》/微雷                    |         | KACIRIE      |
| \[普好雷\] 目擊者 好但不會看第二次                  | 20      | cappa        |
| \[普雷\] 點評《絕境之南》：想贖罪，就留下來         |         | KACIRIE      |
| \[ 算好雷\] 攻殼機動隊                              | 19      | cw56983      |
| \[ 問片\] 眼前的壞人不是壞人                        | 2       | a1322313     |
| \[新聞\] 最強老爸喪妻8年「聽見她說話」　如戲人      |         | huanglove    |
| Re: \[討論\] 玩命關頭紅在哪                         | 18      | Kobe2630     |
| \[問片\] 提到校園霸凌的同志電影                     | 16      | itwitb       |
| 〔LIVE〕CINEMAX 太陽帝國                            | 3       | HellKitty    |
| \[討論\] 【安娜貝爾：造孽】中文官方預告 釋出        | 31      | MyAll        |
| \[請益\] 本能寺大飯店vs生日卡片                     | 13      | baozi0329    |
| \[普雷\] 雙生姊魅 Let Her Out                       |         | mysmalllamb  |
| (本文已被刪除) \[vincentgotu\]                      |         | -            |
| \[普雷\] 描寫生動的寶貝老闆                         | 5       | blacktooth   |
| \[選片\] 攻殼vs金剛vs異星智慧                       | 37      | AE35         |
| \[新聞\] 蘇有朋 《嫌疑人》打趴好萊塢片 一夜捲2.     | 12      | huanglove    |
| \[好雷\] 目擊者                                     | 20      | innocent8675 |
| \[普雷\]《生日卡片》，做自己人生中的主角。          | 2       | a122239      |
| \[好雷\] 我和我的冠軍女兒 Dangal                    | 31      | BMay         |
| \[普雷\] 嫌疑犯X的獻身(中國版)                      | 14      | kmwace       |

解釋爬蟲結果
------------

``` r
##install.packages("jsonlite")
library(jsonlite)
myjson <- toJSON(dataframeAll)
str(dataframeAll)
```

    ## 'data.frame':    220 obs. of  3 variables:
    ##  $ title  : Factor w/ 208 levels "\n\t\t\t\n\t\t\t\t(本文已被刪除) <Eddward>\n\t\t\t\n\t\t\t",..: 6 2 10 19 7 1 16 13 3 18 ...
    ##  $ PushNum: Factor w/ 48 levels "","1","10","13",..: 2 11 5 15 3 11 8 4 6 5 ...
    ##  $ Author : Factor w/ 175 levels "-","ADIMM","andrew0621",..: 3 1 14 8 7 1 6 12 11 17 ...

``` r
table(dataframeAll$ Author)
```

    ## 
    ##            -        ADIMM   andrew0621     chyilian    engineer1 
    ##           15            1            1            1            1 
    ##    harry7319       jkuhih      kkaicd1     laiyuhao   nurais1127 
    ##            1            1            1            1            1 
    ##        oaboy     peter220     riceberg     rrouyyin  samuel60303 
    ##            1            2            1            1            1 
    ##       Scutum   StarLeauge      yesport    yylin3266      a122239 
    ##            1            2            1            1            2 
    ##        azlbf   DantesChen    huanglove   jacktakuya   jarryjarry 
    ##            1            1            3            1            1 
    ##      jay5566        kaleo kickyourface KingKingCold     klaikick 
    ##            9            1            1            1            1 
    ##      linkcat    museangel        MyAll       onlyjh sampsonlu919 
    ##            1            1            5            1            1 
    ##          x77         zkow     bilinear       ck0413   flowergone 
    ##            1            2            1            1            1 
    ##    gmuguruza      j408723  jeanskin420      KACIRIE  KevinMoleaf 
    ##            1            1            1            6            1 
    ##   lady012266   lightlucky  mysmalllamb   neverlight       qpr322 
    ##            1            1            2            1            1 
    ##        soome   uland26922 chinaeatshit      claire8          DDD 
    ##            1            1            1            1            1 
    ##        howpa iam168888888     jazy6804          jpd        kahlo 
    ##            1            1            1            1            1 
    ##       KDlove     killua92          ktl        lowes     nk930043 
    ##            1            1            1            1            1 
    ##    pttnowash       Wall62        XDGEE      y91yi39    a80568911 
    ##            2            1            1            1            1 
    ##     CoffeeBe       cybeth       efairy     hayuyang     itis0423 
    ##            1            1            1            1            1 
    ##    ivorysoap        joyca  lovelydaisy  Mahoutsukai   max6060789 
    ##            1            1            1            1            1 
    ##  mikemagic88  peter080845      redcard  sazanami726      SKnight 
    ##            1            1            1            1            3 
    ##  WalterWhite     ya911019     a1322313         AE35    baozi0329 
    ##            1            1            1            1            1 
    ##   blacktooth         BMay        cappa      cw56983    HellKitty 
    ##            1            1            1            1            1 
    ## innocent8675       itwitb       kmwace     Kobe2630       biboga 
    ##            1            1            1            1            1 
    ##     ck980417        dakkk   freeeedoom     go190214       gyfatz 
    ##            1            1            1            1            2 
    ##        immad      jk10134       kiradu    kirktyler    larrybear 
    ##            1            1            2            1            1 
    ##        Leika     LOLI5566     pelicula       pketam     qn123456 
    ##            1            2            1            1            1 
    ##  takumixnobu    victorway     a3696786     a4839821 archvalkyrie 
    ##            1            1            1            1            1 
    ##     endurant       kyouya    m19871006    NTUlosers         ownr 
    ##            1            1            1            1            1 
    ##     paulyear qwer04230423      Ruthcat     SpkSpawn    stock5566 
    ##            1            1            1            1            1 
    ##      SuperSg       zzz499  bill1478963      brioche         emip 
    ##            1            1            1            1            1 
    ##       flowgo  Ga1axyNote7    green741s  jas1123kimo    jimmy9991 
    ##            1            1            1            1            1 
    ##      lingary   lordyamato  lovemelissa   nothing188 QoHyacinthoQ 
    ##            1            1            1            1            1 
    ##       senria      ss30066       stoneJ        TCPai      thjyrsj 
    ##            1            1            1            1            1 
    ##       ahhway       alista      amx2131 fullmetalyao    justempty 
    ##            1            1            1            1            1 
    ##      koisppq   kurama1984   LF25166234     nerv3890      NiNiHOT 
    ##            1            1            1            1            1 
    ##        signm  Tristan0918       ueiwei       a85405        andey 
    ##            1            1            1            1            1 
    ##      arrakis    chan520cc   guangpiano       LIPOYI   nosweating 
    ##            2            1            1            1            1 
    ##         ooic       purist        Rajon     shinbird          uus 
    ##            1            1            1            1            1

(1)總共爬出220 篇文章，裡面共有3個變數:title、PushNum、Author (2)沒有名字的作者最多，共有15篇沒屬名的文章，有屬名的文章以jay5566的文章最多，共9篇

前30頁vs.後30頁爬蟲結果&解釋
----------------------------

``` r
dataframePAll1=NULL
dataframePAll2=NULL
for(i in 1:30){
  url=paste0("http://www.ptt.cc/bbs/movie/index",i,".html",sep='')
  PTT_PushNum = read_html(url) %>% html_nodes(".nrec") %>% html_text()
  dataframeP1 = data.frame(PushNum = PTT_PushNum)
  dataframePAll1<-rbind(dataframePAll1,dataframeP1)
}
for(i in 5270:5300){
  url=paste0("http://www.ptt.cc/bbs/movie/index",i,".html",sep='')
  PTT_PushNum = read_html(url) %>% html_nodes(".nrec") %>% html_text()
  dataframeP2 = data.frame(PushNum = PTT_PushNum)
  dataframePAll2<-rbind(dataframePAll2,dataframeP2)
}
table(dataframePAll1)
```

    ## dataframePAll1
    ##     1 12 16  2 27  3  4  5  6 67  9 10 15 36  7  8 14 22 11 29 爆 20 23 18 
    ## 95 90  7  3 93  2 66 56 54 24  1 11  9  4  1 23 25  5  2  5  1  1  3  3  1 
    ## 19 31 13 17 24 21 30 28 
    ##  1  1  4  3  2  2  1  1

``` r
table(dataframePAll2)
```

    ## dataframePAll2
    ##    10 19  2  3 38  5  6  7  8  9  1 14 15 16 23 26 28 39 60 17 18 27  4 40 
    ## 62 17 10 41 38  4 32 31 36 23 23 34 18 11 10  9  4  5  2  2 10 12  5 33  2 
    ## 77 爆 43 65 25 29 45 20 22 34 36 37 47 49 53 11 35 12 55 X1 64 13 32 57 61 
    ##  1 12  3  2  4  3  3 10  7  3  4  4  4  2  2 13  1 11  3  1  1 11  3  2  1 
    ## 21 24 69 30 44 79 31 X2 50 33 59 42 58 51 X3 97 67 56 
    ##  5  5  1  2  3  1  4  1  1  2  1  1  2  1  1  1  1  1

dataframePAll1裡面存放的是最舊的30頁文章的推文數，dataframePAll2裡面存放的是最新的30頁文章推文數(也就是最近的30篇文章)，由table()的數量統計來看最舊與最新的推文數，即使PTT現在有點落寞了，但是推噓文數卻比以前多，可以推測出，最近的人們比較會表達他們對文章的感覺，喜歡的話就會推那篇文章，甚至在dataframePAll2裡推文數超過100個的文章也高達12篇(在PTT裡以"爆"來表示)，此外，在dataframePAll2裡也有篇噓文數超過30個的文章(在PTT裡以"X3"來表示)，由此推測現在的人們比較會對作者表達他們對此文章的感覺

228連假爬蟲結果&解釋
--------------------

``` r
dataframeDateAll=NULL
for(i in 5151:5180){
  url=paste0("http://www.ptt.cc/bbs/movie/index",i,".html",sep='')
  PTT_Date = read_html(url) %>% html_nodes(".date") %>% html_text()
  dataframeDate = data.frame(Date = PTT_Date)
  dataframeDateAll<-rbind(dataframeDateAll,dataframeDate)
}
table(dataframeDateAll$ Date)
```

    ## 
    ##  2/22  2/23  2/24  2/25  2/26  2/27  2/28  3/01  3/02 
    ##    12    57    65    61    83   101   126    87     8

2/25-2/28為本國的228假期的四天連假，此段落程式碼是用來分析發文的時間，很明顯的，在2/27、2/28達到了發文數的巔峰，由此數據可推測，許多ppt的用戶在2/25當天尚未真正的放假，直到2/27、2/28兩天才有較空閒的時間上PTT
