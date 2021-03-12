### 分类
{: id="20210308181939-b980dr9" updated="20210308181955"}

* {: id="20210308182001-xnh9d05"}传统检测
  {: id="20210308182001-ijg7fnm" updated="20210308182004"}
* {: id="20210308182004-8o233h4"}实例分割(聚类 )
  {: id="20210308182004-14qp8dw" updated="20210308182019"}
* {: id="20210308182028-gv4u8f5"}语义分割(预先定义好检测线 像素级检测 主要)
  {: id="20210308182028-r8lcrco" updated="20210308182146"}
{: id="20210308181955-qjrzdcy" updated="20210308182001"}

目前使用深度学习算法进行的方向主要有
{: id="20210310131312-b799i8t" updated="20210310131709"}

* {: id="20210310131711-vuy9cju"}图像分割处理后通过聚类或者曲线拟合的方式进行后处理(像素即别分割)
  {: id="20210310131711-8g7b9h7" updated="20210310133357"}
* {: id="20210310131812-lm7nya5"}
  * {: id="20210310131814-tlwbdho"}图像分割在处理长细的物体性能影响比较大(基于密度分割)
    {: id="20210310131814-uk3usys" updated="20210310133219"}
  * {: id="20210310133041-xb4gina"}SCNN
    {: id="20210310133041-xucjbqy" updated="20210310133039"}
  {: id="20210310131811-fqc2xor" updated="20210310131814"}
{: id="20210310131710-s0t9ku9" updated="20210310133042"}

* {: id="20210310133118-sr6tfjl"}ENet-SAD,引入自注意力机制
  {: id="20210310133118-vkpdgq4" updated="20210310133139"}
* {: id="20210310133358-4pvf99e"}PINet 提取稀疏点进行处理来提高处理速度
  {: id="20210310133358-ti6e8io" updated="20210310133853"}
* {: id="20210310134117-p62zwu6"}Poly-LaneNet 将车道线检测认为多项式回归问题(忽略全局信息,曲率较大的路线预测问题)
  {: id="20210310134117-j5y319y" updated="20210310134611"}
{: id="20210310131552-pw4j6qc" updated="20210310134118"}


{: id="20210312133454-xm57jci" updated="20210312132402"}

attention layer:
{: id="20210312133454-7wwi12l" updated="20210312133502"}

![selfattentionlayer.png](assets/attention-layer.png)
{: id="20210312133503-si9fb8y" updated="20210312133520"}

{: id="20210312133502-h9wz1kf" updated="20210312133502"}


{: id="20210312133454-9sy7s4q" updated="20210312133454"}


{: id="20210312133455-oqcuwpf" updated="20210312133454"}

self-attention
{: id="20210310134940-7yeolzy" updated="20210312133455"}

{: id="20210312133243-4nh1h4t" updated="20210312132402"}

![selfattentionlayer.png](assets/slef-attention-layer-2.png)
{: id="20210312133242-vfieomt" updated="20210312133346"}

![selfattentionlayer.png](assets/self-attention-layer.png)
{: id="20210312132402-l3mfvne" updated="20210312132838"}

{: id="20210312133750-qvk27nr" updated="20210312133748"}

![selfattentionlayer.png](assets/self-attention-layer-3.png)
{: id="20210312133738-rhfkcro" updated="20210312133805"}

{: id="20210312133742-kui257y"}


{: id="20210308181939-xa4vtt3" type="doc"}
