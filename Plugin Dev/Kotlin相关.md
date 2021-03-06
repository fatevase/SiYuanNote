# Kotlin
{: id="20210228130037-bwivh9g" updated="20210228130044"}

#### 简介
{: id="20210228130200-41nmdfe" updated="20210228130206"}

目前Kotlin语法与swift十分相似,打算开发ios相关软件,在学习kotlin同时也为之后的mac.ios上的相关开发作准备
{: id="20210228130037-8h8gcy7" updated="20210228130200"}

{: id="20210228130251-97lx2ex" updated="20210227143835"}

## kotlin in vscode
{: id="20210228130252-9bh7b7b" updated="20210228130320"}

### kotlin环境安装
{: id="20210228130349-4gwk268" updated="20210228130355"}

本人还是喜欢使用vscode,为了使用kotlin,首先我们需要安装对应的环境
{: id="20210227143835-vwk3f9t" updated="20210228130349"}

> https://github.com/JetBrains/kotlin
> {: id="20210228130341-g06y1r1"}
{: id="20210227143858-n20m09g" updated="20210228130341"}

下载放到本地文件夹下如`~`
{: id="20210227143943-o7zoryk" updated="20210227144019"}


{: id="20210228130357-7iqpacg" updated="20210227144657"}

### vscode 相关配置
{: id="20210228130344-zgw1yzc" updated="20210228130410"}

对于vscode我们需要的插件有
{: id="20210227144020-qj86c9x" updated="20210228130344"}

* {: id="20210227144109-szzeyif"}kotlin language(mathiasfrohlich) 语言支持
  {: id="20210227144109-lnxkqo5" updated="20210227144207"}
* {: id="20210227144135-w5jqq5m"}code runner(jun han) 代码运行
  {: id="20210227144135-uvkhacy" updated="20210227144211"}
{: id="20210227144037-egjq344" updated="20210227144040"}

配置对应的sttings让code runner可以找到我们本地的kotlinc
{: id="20210227143857-33bxtos" updated="20210227144241"}

```
		//setting about kotlin
		"code-runner.executorMapByFileExtension": {
			".kt": "cd $dir && ~/software/kotlin/kotlinc/bin/kotlinc $fileName -include-runtime -d $fileNameWithoutExt.jar && java -jar $fileNameWithoutExt.jar",
		},
```
{: id="20210227144248-k05h7rb" updated="20210227144248"}

测试
{: id="20210227144258-pz4cta2" updated="20210227144302"}

```kotlin
# hello.kt
fun main() {
    println("Hello World")
}
```
{: id="20210227144302-1lwhm5o" updated="20210227144318"}


{: id="20210228130417-4l94r6y" updated="20210227161130"}


{: id="20210228130418-juje07t" updated="20210228130417"}

### gradle包管理配置与使用
{: id="20210228130418-5ck6vho" updated="20210228130437"}

vscode 配置 gradle
{: id="20210227161122-j9ddymh" updated="20210228130418"}

vscode 在使用gradle 首先确保安装对应插件
{: id="20210227161130-j7bymij" updated="20210227175405"}

**Gradle Extension Pack**
{: id="20210227175424-3gc942c" updated="20210227175425"}

![gradleplugins.png](assets/gradle-plugins.png)
{: id="20210227175427-b5d1zy3" updated="20210228130851"}

之后在工作空间添加相关的设置,让其识别到.gradlew 和build.gradle
{: id="20210227175520-jhj3n5b" updated="20210227175603"}

```

		"gradle.nestedProjects": true,
```
{: id="20210227175604-1b1ryam" updated="20210227175615"}


{: id="20210228130443-9of0b5i" updated="20210227175657"}

#### 为了简便,我们并不安装gradle环境,而是使用gradlew进行项目的安装管理,
{: id="20210228130442-8ujebst" updated="20210228130509"}

项目文件夹下新建`gradlew`
{: id="20210227175545-juaob3h" updated="20210228130514"}

```
#!/usr/bin/env sh

##############################################################################
##
##  Gradle start up script for UN*X
##
##############################################################################

# Attempt to set APP_HOME
# Resolve links: $0 may be a link
PRG="$0"
# Need this for relative symlinks.
while [ -h "$PRG" ] ; do
    ls=`ls -ld "$PRG"`
    link=`expr "$ls" : '.*-> \(.*\)$'`
    if expr "$link" : '/.*' > /dev/null; then
        PRG="$link"
    else
        PRG=`dirname "$PRG"`"/$link"
    fi
done
SAVED="`pwd`"
cd "`dirname \"$PRG\"`/" >/dev/null
APP_HOME="`pwd -P`"
cd "$SAVED" >/dev/null

APP_NAME="Gradle"
APP_BASE_NAME=`basename "$0"`

# Add default JVM options here. You can also use JAVA_OPTS and GRADLE_OPTS to pass JVM options to this script.
DEFAULT_JVM_OPTS='"-Xmx64m" "-Xms64m"'

# Use the maximum available, or set MAX_FD != -1 to use that value.
MAX_FD="maximum"

warn () {
    echo "$*"
}

die () {
    echo
    echo "$*"
    echo
    exit 1
}

# OS specific support (must be 'true' or 'false').
cygwin=false
msys=false
darwin=false
nonstop=false
case "`uname`" in
  CYGWIN* )
    cygwin=true
    ;;
  Darwin* )
    darwin=true
    ;;
  MINGW* )
    msys=true
    ;;
  NONSTOP* )
    nonstop=true
    ;;
esac

CLASSPATH=$APP_HOME/gradle/wrapper/gradle-wrapper.jar


# Determine the Java command to use to start the JVM.
if [ -n "$JAVA_HOME" ] ; then
    if [ -x "$JAVA_HOME/jre/sh/java" ] ; then
        # IBM's JDK on AIX uses strange locations for the executables
        JAVACMD="$JAVA_HOME/jre/sh/java"
    else
        JAVACMD="$JAVA_HOME/bin/java"
    fi
    if [ ! -x "$JAVACMD" ] ; then
        die "ERROR: JAVA_HOME is set to an invalid directory: $JAVA_HOME

Please set the JAVA_HOME variable in your environment to match the
location of your Java installation."
    fi
else
    JAVACMD="java"
    which java >/dev/null 2>&1 || die "ERROR: JAVA_HOME is not set and no 'java' command could be found in your PATH.

Please set the JAVA_HOME variable in your environment to match the
location of your Java installation."
fi

# Increase the maximum file descriptors if we can.
if [ "$cygwin" = "false" -a "$darwin" = "false" -a "$nonstop" = "false" ] ; then
    MAX_FD_LIMIT=`ulimit -H -n`
    if [ $? -eq 0 ] ; then
        if [ "$MAX_FD" = "maximum" -o "$MAX_FD" = "max" ] ; then
            MAX_FD="$MAX_FD_LIMIT"
        fi
        ulimit -n $MAX_FD
        if [ $? -ne 0 ] ; then
            warn "Could not set maximum file descriptor limit: $MAX_FD"
        fi
    else
        warn "Could not query maximum file descriptor limit: $MAX_FD_LIMIT"
    fi
fi

# For Darwin, add options to specify how the application appears in the dock
if $darwin; then
    GRADLE_OPTS="$GRADLE_OPTS \"-Xdock:name=$APP_NAME\" \"-Xdock:icon=$APP_HOME/media/gradle.icns\""
fi

# For Cygwin or MSYS, switch paths to Windows format before running java
if [ "$cygwin" = "true" -o "$msys" = "true" ] ; then
    APP_HOME=`cygpath --path --mixed "$APP_HOME"`
    CLASSPATH=`cygpath --path --mixed "$CLASSPATH"`

    JAVACMD=`cygpath --unix "$JAVACMD"`

    # We build the pattern for arguments to be converted via cygpath
    ROOTDIRSRAW=`find -L / -maxdepth 1 -mindepth 1 -type d 2>/dev/null`
    SEP=""
    for dir in $ROOTDIRSRAW ; do
        ROOTDIRS="$ROOTDIRS$SEP$dir"
        SEP="|"
    done
    OURCYGPATTERN="(^($ROOTDIRS))"
    # Add a user-defined pattern to the cygpath arguments
    if [ "$GRADLE_CYGPATTERN" != "" ] ; then
        OURCYGPATTERN="$OURCYGPATTERN|($GRADLE_CYGPATTERN)"
    fi
    # Now convert the arguments - kludge to limit ourselves to /bin/sh
    i=0
    for arg in "$@" ; do
        CHECK=`echo "$arg"|egrep -c "$OURCYGPATTERN" -`
        CHECK2=`echo "$arg"|egrep -c "^-"`                                 ### Determine if an option

        if [ $CHECK -ne 0 ] && [ $CHECK2 -eq 0 ] ; then                    ### Added a condition
            eval `echo args$i`=`cygpath --path --ignore --mixed "$arg"`
        else
            eval `echo args$i`="\"$arg\""
        fi
        i=`expr $i + 1`
    done
    case $i in
        0) set -- ;;
        1) set -- "$args0" ;;
        2) set -- "$args0" "$args1" ;;
        3) set -- "$args0" "$args1" "$args2" ;;
        4) set -- "$args0" "$args1" "$args2" "$args3" ;;
        5) set -- "$args0" "$args1" "$args2" "$args3" "$args4" ;;
        6) set -- "$args0" "$args1" "$args2" "$args3" "$args4" "$args5" ;;
        7) set -- "$args0" "$args1" "$args2" "$args3" "$args4" "$args5" "$args6" ;;
        8) set -- "$args0" "$args1" "$args2" "$args3" "$args4" "$args5" "$args6" "$args7" ;;
        9) set -- "$args0" "$args1" "$args2" "$args3" "$args4" "$args5" "$args6" "$args7" "$args8" ;;
    esac
fi

# Escape application args
save () {
    for i do printf %s\\n "$i" | sed "s/'/'\\\\''/g;1s/^/'/;\$s/\$/' \\\\/" ; done
    echo " "
}
APP_ARGS=`save "$@"`

# Collect all arguments for the java command, following the shell quoting and substitution rules
eval set -- $DEFAULT_JVM_OPTS $JAVA_OPTS $GRADLE_OPTS "\"-Dorg.gradle.appname=$APP_BASE_NAME\"" -classpath "\"$CLASSPATH\"" org.gradle.wrapper.GradleWrapperMain "$APP_ARGS"

exec "$JAVACMD" "$@"

```
{: id="20210227175657-2hflu30" updated="20210228130525"}


{: id="20210228130547-vy08yf3" updated="20210228130547"}

此时该项目已经支持gradle了
{: id="20210228130520-l5m84mw" updated="20210228130547"}


{: id="20210228130548-4cvp2z9" updated="20210228130520"}

#### 创建build文件
{: id="20210228130548-87b1zm3" updated="20210228130602"}

新建`build.gradle`
{: id="20210227175831-bk9xlr9" updated="20210228130605"}

```
// 定义一些插件
plugins {
	id 'java'
}

group = 'cc.squirtle'
version = '0.0.1-SNAPSHOT'
//jdk版本声明
sourceCompatibility = '14'

//配置国内源和自己需要的其他源
// 使用的仓库优先级
repositories {
　　	//mavenCentral()
	//minecraftapi源
        maven {
        url "https://hub.spigotmc.org/nexus/content/repositories/snapshots"
        }
	//国内源
        maven {
            url 'https://maven.aliyun.com/repository/google'
        }
        maven {
            url 'https://maven.aliyun.com/repository/public'
        }
        maven {
            url 'https://maven.aliyun.com/repository/jcenter'
        }
}

dependencies {
	//自己依赖的相关包
	compileOnly "org.spigotmc:spigot-api:1.16.5-R0.1-SNAPSHOT"
}

```
{: id="20210227175843-75f3lop" updated="20210227180457"}

重启vscode等插件识别项目后自动安装.gradle相关内容
{: id="20210227175743-bzhxrur" updated="20210227175851"}

![image.png](assets/gradle-files-tree.png)
{: id="20210227175816-a5awgb6" updated="20210228131019"}

* {: id="20210228130651-btknh7a"}我们在build.gradle进行包依赖等管理
  {: id="20210228130651-96mv01d" updated="20210228130653"}
* {: id="20210228130654-7sbw6kl"}使用gradlew对项目进行打包
  {: id="20210228130654-x361noj" updated="20210228130654"}
* {: id="20210228130658-1mm8kld"}.gradle 为gradlew生成文件
  {: id="20210228130658-w8gfsnc" updated="20210228130713"}
* {: id="20210228130714-bhl4uff"}settings.gradle可以对项目进行一些基本配置
  {: id="20210228130714-sl2a2sh" updated="20210228130727"}
* {: id="20210228130730-mnwfs9v"}build 为打包编译文件
  {: id="20210228130730-7czcxpz" updated="20210228130739"}
{: id="20210228130617-j51ws65" updated="20210228130651"}

最终目录格式,其中通过`build`打包的jar包存放在 build/lib中
{: id="20210227181159-rkxeebo" updated="20210228130617"}


{: id="20210228130744-d0qyfp7" updated="20210228124950"}

### Kotlin使用gradle
{: id="20210228130744-du0gt82" updated="20210228130756"}

以下针对kotlin 用gradle进行打包jar
{: id="20210227181221-ui91blz" updated="20210228130744"}

```
import org.jetbrains.kotlin.gradle.tasks.KotlinCompile

plugins {

	kotlin("jvm") version "1.4.30"
}


group = "cc.squirtle"
version = "0.1"
java.sourceCompatibility = JavaVersion.VERSION_14

repositories {
		maven{url = uri("https://hub.spigotmc.org/nexus/content/repositories/snapshots/")}
		maven{url = uri("https://maven.aliyun.com/repository/google")}
		maven{url = uri("https://maven.aliyun.com/repository/public")}
		maven{url = uri("https://maven.aliyun.com/repository/jcenter")}
}

dependencies {
	compileOnly("org.spigotmc:spigot-api:1.16.5-R0.1-SNAPSHOT")
	implementation("org.jetbrains.kotlin:kotlin-reflect")
	implementation("org.jetbrains.kotlin:kotlin-stdlib-jdk8")
}

tasks.withType<KotlinCompile> {
	kotlinOptions {
		freeCompilerArgs = listOf("-Xjsr305=strict")
		jvmTarget = "14"
	}
}


```
{: id="20210228124950-w7plfgk" updated="20210228125027"}

{: id="20210228130236-l25lfzs"}

## 相关参考
{: id="20210228130158-9pqeu22" updated="20210228130224"}

https://www.jianshu.com/p/90158cdc6d18
{: id="20210227143834-xewept6" updated="20210228130037"}

{: id="20210228130241-01o3g99"}

{: id="20210228130239-8mvm366"}

{: id="20210228130240-3k9vruc"}

{: id="20210228130239-wuav5fr"}


{: id="20210227143834-hlch7fc" type="doc"}
