https://openjdk.java.net/install/
{: id="20210125121245-wud6woa"}

{: id="20210206234419-dr9umc9"}

sudo apt-get install openjdk-14-realease-jdk
{: id="20210125121253-8qydvan"}

{: id="20210206234423-aovw4lc"}

### vscode 安装 maven
{: id="20210206234423-lcon37p"}

{: id="20210206234438-9p1vvj2"}

下载maven :https://maven.apache.org/download.cgi
{: id="20210206234438-87yiies"}


{: id="20210206234932-m7jovj9"}

配置aliyun镜像
{: id="20210206234915-klk9tp8"}

maven/conf/settings.xml
{: id="20210206234930-twu66e2"}

找到mirrors ,并添加mirror,具体如下
{: id="20210206234944-i8gxi7m"}

```xml
<mirrors>
	<mirror>
		<id>alimaven</id>
		<mirrorOf>central</mirrorOf>
		<name>aliyun maven</name>
		<url>http://maven.aliyun.com/nexus/content/repositories/central/</url>
	    </mirror>
</mirrors>
```
{: id="20210206235033-jwsy6xf"}

配置maven路径:
{: id="20210206234455-ndrzv5s"}

maven.executable.path
{: id="20210206234419-irx39zs"}

-> ~/software/maven/bin/mvn
{: id="20210206234511-xb3gmme"}

{: id="20210206235333-zy3lcix"}

之后就可以通过maven生成一个初始的maven项目了
{: id="20210206235331-z657f05"}

> *Choose org.apache.maven.archetypes:maven-archetype-quickstart version:*
> *1: 1.0-alpha-1*
> *2: 1.0-alpha-2*
> *3: 1.0-alpha-3*
> *4: 1.0-alpha-4*
> *5: 1.0*
> *6: 1.1*
> *Choose a number: 6: (直接回车)*
> *Define value for property 'groupId': : cnblogs （可暂时先理解成类似package或namespace的名称，通常我们填写组织机构名称缩写）*
> *Define value for property 'artifactId': : maven-hello-world （组件名称，可暂时理解成项目名称）*
> *Define value for property 'version':  1.0-SNAPSHOT: : （版本号，直接回车，默认1.0-SNAPSHOT）*
> *Define value for property 'package':  cnblogs: : （打包后的jar文件名，相当于.net中项目最后生成的程序集dll名称）*
> *Confirm properties configuration:*
> *groupId: cnblogs*
> *artifactId: maven-hello-world*
> *version: 1.0-SNAPSHOT*
> *package: cnblogs*
> {: id="20210206235401-bhlc12q"}
>
> * {: id="20210206235401-upqs9q7"}Y: :  (直接回车确认)*
>   {: id="20210206235401-93vml3e"}
> {: id="20210206235401-46dxorz"}
>
> {: id="20210206235401-flmt03o"}
{: id="20210206235358-i24b33r"}


{: id="20210125121245-4wzpfiv" type="doc"}
