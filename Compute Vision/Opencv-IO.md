imread	(const String & 	filename,
int 	flags = IMREAD_COLOR)

* 返回值，Mat 类型， 即返回读取的图像，读取图像失败时返回一个空的矩阵对象（Mat::data == NULL)
* 参数 1 filename, 读取的图片文件名，可以使用相对路径或者绝对路径，但必须带完整的文件扩展名（图片格式后缀）
* 参数 2 flags, 一个读取标记，用于选择读取图片的方式，默认值为 IMREAD_COLOR，flag 值的设定与用什么颜色格式读取图片有关

> python 种 flags 取之在[-1,4]，flag 默认为 1
> 分别对应
> -1:八深度，原通道
> 0:八深度，一通道
> 1:八深度，三通道
> 2:原深度，一通道
> 3:八深度，通道


{: id="20201120095601-h0d6yey" type="doc"}
