CV_EXPORTS_W void filter2D( InputArray src,
OutputArray dst,
int ddepth,
InputArray kernel,
Point anchor=Point(-1,-1),
double delta=0,
int borderType=BORDER_DEFAULT );

* InputArray src: 输入图像
* OutputArray dst: 输出图像，和输入图像具有相同的尺寸和通道数量
* int ddepth: 目标图像深度，如果没写将生成与原图像深度相同的图像。
* InputArray kernel: 卷积核（或者是相关核），一个单通道浮点型矩阵。如果想在图像不同的通道使用不同的 kernel，可以先使用 split()函数将图像通道事先分开。
* Point anchor: 内核的基准点(anchor)，其默认值为(-1,-1)说明位于 kernel 的中心位置。基准点即 kernel 中与进行处理的像素点重合的点。
* double delta: 在储存目标图像前可选的添加到像素的值，默认值为 0
* int borderType: 像素向外逼近的方法，默认值是 BORDER_DEFAULT，即对全部边界进行计算。

该函数使用于任意线性滤波器的图像，支持就地操作。当其中心移动到图像外，函数可以根据指定的边界模式进行插值运算。函数实质上是计算 kernel 与图像的相关性而不是卷积：
![](Pasted%20image%2020201106221359.png)

$$
𝚍𝚜𝚝(𝑥,𝑦)=\sum_{0≤𝑦′<𝚔𝚎𝚛𝚗𝚎𝚕.𝚛𝚘𝚠𝚜,0≤𝑥′<𝚔𝚎𝚛𝚗𝚎𝚕.𝚌𝚘𝚕𝚜}𝚔𝚎𝚛𝚗𝚎𝚕(𝑥′,𝑦′)∗𝚜𝚛𝚌(𝑥+𝑥′−𝚊𝚗𝚌𝚑𝚘𝚛.𝚡,𝑦+𝑦′−𝚊𝚗𝚌𝚑𝚘𝚛.𝚢)
$$

也就是说 kernel 并不是中心点的镜像，如果需要一个正真的卷积，使用函数 flip()并将中心点设置为(kernel.cols - anchor.x - 1, kernel.rows - anchor.y -1).

> ddepth 输入值为-1 时，目标图像和原图像深度保持一致。


{: id="20201120095601-2ylir28" type="doc"}
