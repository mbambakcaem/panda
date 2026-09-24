## press-scraper
Collecting the seven main desks of each Korean daily and pulling the headline keywords out of them.
- seven desks per outlet: politics, business, world, society, culture, entertainment, sport
- keyword mining per desk

### 1. Landing page per outlet
- chosun: https://www.chosun.com/
    - article path: https://www.chosun.com/<desk>/<sub>/yyyy/mm/dd/<id>/
    - id shape: [0-9A-Z]{26}

- joongang: https://www.joongang.co.kr/
    - article path: https://www.joongang.co.kr/article/<id>
    - id shape: [0-9]{8} e.g. 25180554

- donga: https://www.donga.com/news/
    - date param: ymd=20230801
    - article path: https://www.donga.com/news/<desk>/article/all/yyyymmdd/<id>/[1|2] e.g. 20230727/120437634/1
    - id shape: [0-9]{9}

- seoul: https://www.seoul.co.kr/news/newsList.php?section=
    - date param: date=2023-08-01
    - article path: https://www.seoul.co.kr/news/newsView.php?id=<id>
    - id shape: yyyymmdd[0-9]{6} e.g. 20230727500072

- khan: https://www.khan.co.kr/
    - article path: https://khan.co.kr/<desk>/<sub>/article/<id>
    - id shape: yyyymmddHHMM[0-9]{3} e.g. 202307262158001

- maeil: https://news.imaeil.com/
    - article path: https://news.imaeil.com/page/view/<id>
    - id shape: yyyymmddHHMMSSf e.g. 2023072610292725460

- hani: https://www.hani.co.kr/arti/
    - article path: https://www.hani.co.kr/arti/\<desk>/\<sub>/\<id>.html
    - id shape: [0-9]{7}

- hankook: https://www.hankookilbo.com/
    - article path: https://www.hankookilbo.com/News/Read/\<id>
    - id shape: [0-9A-Z]{20} e.g. A2023072715420004839

### 2. The seven desks
- politics, business, world, society, culture, entertainment, sport

### 3. Sub-desk map per outlet
- mapping sheet: data/desk_map.xlsx

### 3. Page markup notes
#### 3-1. chosun
> ##### - listing page
>- url: https://www.chosun.com/\<desk>/\<sub>/
>>1. feed block
>>- tag: div
>>- class: story-feed
>>2. headline
>>- tag: a
>>- class: story-card__headline | box--margin-none text--black font--secondary h4 text__link--color
>>3. standfirst
>>- tag: div
>>- class: story-card-component story-card__deck | text--grey-60 font--primary font--size-sm-14 font--size-md-14 text--line-height-1.43 text--overflow-ellipsis
>>4. article link
>>- tag: a
>>- attr: href, e.g. /\<desk>/\<sub>/\<yyyy>/\<mm>/\<dd>/\<id>
> ##### - article page
>- url: https://www.chosun.com/\<desk>/\<sub>/\<yyyy>/\<mm>/\<dd>/\<id>
>>1. headline
>>- tag: h1
>>- class: article-header__headline
>>2. body copy
>>- tag: section
>>- class: article-body