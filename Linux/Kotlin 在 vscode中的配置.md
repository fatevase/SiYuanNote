https://www.jianshu.com/p/90158cdc6d18
{: id="20210227143834-xewept6" updated="20210227143835"}

{: id="20210227143835-vwk3f9t" updated="20210227143835"}

为了使用kotlin,首先我们需要安装对应的环境
{: id="20210227143835-07y2bff" updated="20210227143857"}

https://github.com/JetBrains/kotlin
{: id="20210227143858-n20m09g" updated="20210227143942"}

{: id="20210227143943-nkmo97x" updated="20210227143942"}

下载放到本地文件夹下如`~`
{: id="20210227143943-o7zoryk" updated="20210227144019"}

对于vscode我们需要的插件有
{: id="20210227144020-qj86c9x" updated="20210227144657"}

* {: id="20210227144109-szzeyif"}kotlin language(mathiasfrohlich) 语言支持
  {: id="20210227144109-lnxkqo5" updated="20210227144207"}
* {: id="20210227144135-w5jqq5m"}code runner(jun han) 代码运行
  {: id="20210227144135-uvkhacy" updated="20210227144211"}
{: id="20210227144037-egjq344" updated="20210227144040"}

{: id="20210227144212-15dh563"}

配置对应的sttings让code runner可以找到我们本地的kotlinc
{: id="20210227143857-33bxtos" updated="20210227144241"}

```
		//setting about kotlin
		"code-runner.executorMapByFileExtension": {
			".kt": "cd $dir && ~/software/kotlin/kotlinc/bin/kotlinc $fileName -include-runtime -d $fileNameWithoutExt.jar && java -jar $fileNameWithoutExt.jar",
		},
```
{: id="20210227144248-k05h7rb" updated="20210227144248"}

{: id="20210227144257-837v1n3"}

测试
{: id="20210227144258-pz4cta2" updated="20210227144302"}

```kotlin
# hello.kt
fun main() {
    println("Hello World")
}
```
{: id="20210227144302-1lwhm5o" updated="20210227144318"}


{: id="20210227143834-hlch7fc" type="doc"}
