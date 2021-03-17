{: id="20210317164537-llmbv5p"}

### 导入
{: id="20210317164537-0cqnaxy" updated="20210317164544"}

{: id="20210317164536-dbazg8u" updated="20210317164537"}

```python
import pandas as pd
pd.plotting.register_matplotlib_converters()
import matplotlib.pyplot as plt
%matplotlib inline
import seaborn as sns
print("Setup Complete")
```
{: id="20210317164522-wk2k6sm" updated="20210317164528"}

{: id="20210317164559-9qeknb2"}

### ReadData
{: id="20210317164559-1ltjwxj" updated="20210317164609"}

```python
import os 
file_path = "./path/to/file.csv"
pd.read_csv(file_path,index_col="index_name")
```
{: id="20210317164609-6rxcvkm" updated="20210317165008"}

{: id="20210317164559-1pevtia"}

### LinePlot
{: id="20210317164532-d105iqr" updated="20210317164554"}

```python
plt.title("line title")
sns.lineplot(data)
```
{: id="20210317165012-c472014" updated="20210317165100"}

{: id="20210317165057-nyc0wdq"}

### ChartPlot
{: id="20210317164548-zk9rauv" updated="20210317165108"}

{: id="20210317165109-p974ujb"}

{: id="20210317170759-dpotq3c"}

### 计算数值
{: id="20210317165108-tulsup1" updated="20210317170805"}

{: id="20210317170807-wm2kp24" updated="20210317170807"}

平均值
{: id="20210317170805-fjy105u" updated="20210317170816"}

> data.mean(axis=1)#axis 0 means cols，1 = rows
> {: id="20210317170816-9xt3dbs" updated="20210317170825"}
{: id="20210317170816-v6jt9dh" updated="20210317170834"}

排序
{: id="20210317171311-cdmg5o3" updated="20210317171316"}

> ```python
> # 按指定的一列排序
> lists.sort_values(by="Price",inplace=True,ascending=False)
>
> # 指定多列排序(注意：对Worthy列升序，再对Price列降序)，ascending不指定的话，默认是True升序
> lists.sort_values(by=["Worthy","Price"],inplace=True,ascending=[True,False])
> ```
> {: id="20210317171318-78p0dwb" updated="20210317171348"}
{: id="20210317171317-n1xv29d" updated="20210317171318"}

{: id="20210317171839-csuxtle"}

{: id="20210317172705-q3jwkge"}

{: id="20210317172706-gexvnoh"}

### 获取指定数据
{: id="20210317172705-52k14gl" updated="20210317172718"}

{: id="20210317172705-9c2hmah"}

获取对于行
{: id="20210317171840-wpparfw" updated="20210317171845"}

> ign_data.iloc[[uint]] # 获取指定的行(通过数字)
> {: id="20210317171848-j01wchk" updated="20210317171911"}
>
> ign_data.loc[[label_name]] # 获取指定的行(通过指定标签)
> {: id="20210317171958-l0ggwel" updated="20210317172017"}
{: id="20210317171846-4wzj0ms" updated="20210317171958"}

{: id="20210317172721-31mur1m" updated="20210317172721"}

获取对于行名
{: id="20210317172701-fhpznjw" updated="20210317172848"}

> data.index
> {: id="20210317172742-bp2n81e" updated="20210317173021"}
{: id="20210317172732-olarrbz" updated="20210317172742"}

{: id="20210317173005-whvhi2o" updated="20210317172702"}

获取列名:
{: id="20210317172658-m4dpxnx" updated="20210317173010"}

> data.columns
> {: id="20210317173011-2xytq5k" updated="20210317173016"}
{: id="20210317173010-lpdi59p" updated="20210317173011"}

{: id="20210317173434-lh9hijv"}

获取行列最大值(无重复)
{: id="20210317173435-q75tecp" updated="20210317173452"}

> data.idxmax(1) # 计算行的最大值 之后返回index 与 列名
> {: id="20210317173453-yddn1qe" updated="20210317173653"}
>
> data.idxmax(0) # 计算列的最大值 之后返回index 与 列名
> {: id="20210317173632-cu7p5f9" updated="20210317173656"}
{: id="20210317173453-aml7uia" updated="20210317173656"}

{: id="20210317173657-i2s1ovy"}


{: id="20210317164510-ifnkhu1" type="doc"}
