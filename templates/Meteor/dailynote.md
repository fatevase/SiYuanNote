{{ $ppath := nospace (cat "https://gitee.com/zhangjlsjtu/pic/raw/master/picture/diary"  ((randInt 1 4) | toString) ".jpg") }}
{: id="20210111161552-0vrsj2e"}

{{$after := (div ((toDate "2006-01-02" "2021-05-05").Sub now).Hours 24)}}
{: id="20210111214945-sepmjl0" updated="20210226135036"}

{{$week := add (mod (div ((toDate "2006-01-02" "2050-03-13").Sub now).Hours 24) 7) 1}}
{: id="20210113013412-ougpydf"}

![image.png]({{$ppath}})
{: id="20210111161552-vmdtx1b"}

## 🕐 创建时间：{{now | date "2006-01-02 15:04"}} {{last (slice (list "星期六" "星期五" "星期四" "星期三" "星期二" "星期一" "星期天") 0 $week )}}
{: id="20210111161552-25x8q95" style=" box-shadow: -4px 0px 0px 0px ;"}

> 距离 `2021-05-05` 还剩 `{{$after}}` 天
> {: id="20210118002706-lfp7yq1" updated="20210226135031"}
{: id="20210115191841-enx7wea"}

## 🧱((20210217233154-6r71zk3 "Daily work"))-{{now | date "01/02"}}
{: id="20210111215426-n6ic5xb" updated="20210226143610"}

> 第一次日记模板设置方法：为方便使用汇总功能，请进入`/templates/Meteor/`下定制自己的`dailynote`模板
> {: id="20210226143218-g802axk" updated="20210226143447"}
>
> 1. {: id="20210226143424-9ul403n"}新建`Daily work`或者其他名字的页面，在页面里面调用`link`模板（反链提及），然后复制页面的块引用
>    {: id="20210226143424-v0dvuot" updated="20210226143602"}
> 2. {: id="20210226143424-d1pkjgj"}`alt ctrl 0`进入专家模式，找个空白的地方，粘贴块引用.  注意不要动里面的id
>    {: id="20210226143424-g0xpg4r" updated="20210226142038"}
> 3. {: id="20210226143424-le1qqsj"}把`🧱 Daily work`的ID  `((ID "文本"))`替换成你刚刚粘贴的部分的ID
>    {: id="20210226143424-5xti00t" updated="20210226141425"}
> 4. {: id="20210226143424-oswquyi"}`alt ctrl 7` 返回及时渲染模式，删除这段注释。找个空白文档，调用`dailynote`日记模板测试一下
>    {: id="20210226143424-hxaxhzd" updated="20210226143549"}
> {: id="20210226143451-q5cvb7c"}
{: id="20210226143218-hebhyss" updated="20210226143451"}

text
{: id="20210226143641-owbh20s" updated="20210226143735"}

## 📝 ((20210217233336-3akpqfr "Notes"))-{{now | date "01/02"}}
{: id="20210224203954-lr7fja6" updated="20210226143637"}

text
{: id="20210118002650-89v936m" updated="20210226143725"}

## 🎉️ 历史待办
{: id="20210117173634-z3gapm0"}

> 截止至 `{{now | date "2006-01-02 15:04"}} {{last (slice (list "星期六" "星期五" "星期四" "星期三" "星期二" "星期一" "星期天") 0 $week )}}`
> {: id="20210117174348-sb8dow5"}
{: id="20210117174346-yrb35qv"}

!{{select * from blocks where markdown like '%[ ]%' and type = 'l' and root_id != '{{.id}}' order by created DESC limit 3}}
{: id="20210117173702-t5ifomh" updated="20210226144333"}

{{$dayleft := (div ((toDate "2006-01-02" "2022-01-01").Sub now).Hours 24)}}
{: id="20210226144120-msdamtc"}

## 🚴 随机复习
{: id="20210117204808-yqws8cs" updated="20210226143819"}

> 距离 `2022-01-01` 还剩 `{{$dayleft}}` 天，加油！
> {: id="20210117205515-8p7rsx9" updated="20210226144045"}
{: id="20210117205436-61dcsj6"}

!{{SELECT * FROM blocks where type = 'd' and root_id != '{{.id}}' and path not like '%daily%' ORDER BY random() LIMIT 1}}
{: id="20210117204827-z8lk3kf"}

{: id="20210226143756-lb5ob5h"}


{: id="20210111161529-0vkdosg" type="doc"}
