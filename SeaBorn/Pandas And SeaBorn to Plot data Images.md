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

{: id="20210317165108-tulsup1"}


{: id="20210317164510-ifnkhu1" type="doc"}
