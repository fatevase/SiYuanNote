## 读取视频

```cpp
VideoCapture(int 	index,
int 	apiPreference = CAP_ANY 
)
```

```python
#python
<VideoCapture object>	=	cv.VideoCapture(	
filename[, apiPreference]	)

<VideoCapture object>	=	cv.VideoCapture(	
index[, apiPreference]	)
```

* index 为视频摄像头设备id 打开默认摄像头即为0. (当 apiPreference 为 CAP_ANY id 设为 camera_id + domain_offset (CAP_*) 可以有效向后兼容)
* apiPreference	首选的捕获 API 后端,可强制指定特定当读取器
  * cv::CAP_DSHOW
  * cv::CAP_MSMF
  * cv::CAP_V4L.

```python
retval	=	cv.VideoCapture.get(propId)
```

> 返回指定视频属性

#### propid 可用参数

| param  (CAP_PROP_FRAME_*) | define                                                                               |
| ------------------------- | ------------------------------------------------------------------------------------ |
| cv2.VideoCapture.get(0)   | 视频文件的当前位置（播放）以毫秒为单位                            |
| cv2.VideoCapture.get(1)   | 基于以0开始的被捕获或解码的帧索引                                    |
| cv2.VideoCapture.get(2)   | 视频文件的相对位置（播放）：0=电影开始，1=影片的结尾。      |
| cv2.VideoCapture.get(3)   | 在视频流的帧的宽度                                                          |
| cv2.VideoCapture.get(4)   | 在视频流的帧的高度                                                          |
| cv2.VideoCapture.get(5)   | 帧速率 FPS                                                                        |
| cv2.VideoCapture.get(6)   | 编解码的4字-字符代码                                                        |
| cv2.VideoCapture.get(7)   | 视频文件中的所有帧总数                                                    |
| cv2.VideoCapture.get(8)   | 返回对象的格式                                                                |
| cv2.VideoCapture.get(9)   | 返回后端特定的值，该值指示当前捕获模式                            |
| cv2.VideoCapture.get(10)  | 图像的亮度(仅适用于照相机)                                               |
| cv2.VideoCapture.get(11)  | 图像的对比度(仅适用于照相机)                                            |
| cv2.VideoCapture.get(12)  | 图像的饱和度(仅适用于照相机)                                            |
| cv2.VideoCapture.get(13)  | 色调图像(仅适用于照相机)                                                  |
| cv2.VideoCapture.get(14)  | 图像增益(仅适用于照相机)                                                  |
| cv2.VideoCapture.get(15)  | 曝光(仅适用于照相机)                                                        |
| cv2.VideoCapture.get(16)  | 指示是否应将图像转换为RGB布尔标志                                     |
| cv2.VideoCapture.get(17)  | × 暂时不支持                                                                   |
| cv2.VideoCapture.get(18)  | 立体摄像机的矫正标注（目前只有DC1394 v.2.x后端支持这个功能） |

```python
retval	=	cv.VideoCapture.grab()
```

> 从视频文件或捕获设备获取下一帧。

```python
None	=	cv.VideoCapture.release()
```

> 关闭文件或者关闭捕捉当设备

#### 读取视频指定帧数

```python
video_frame = 100
capture.set(cv2.CAP_PROP_POS_FRAMES,video_frame)  #设置要获取的帧号 这里我获取的是第100帧
bl,video_img=capture.read()  #read方法返回一个布尔值和一个视频帧。若帧读取成功，则返回True
```

---

## 保存视频

```cpp
cv::VideoWriter::VideoWriter	(	const String & 	filename,
int 	fourcc,
double 	fps,
Size 	frameSize,
bool 	isColor = true 
)	
```

```python
#Python:
<VideoWriter object>	=	cv.VideoWriter(		)
<VideoWriter object>	=	cv.VideoWriter(	filename, fourcc, fps, frameSize[, isColor]	)
<VideoWriter object>	=	cv.VideoWriter(	filename, apiPreference, fourcc, fps, frameSize[, isColor]	)
<VideoWriter object>	=	cv.VideoWriter(	filename, fourcc, fps, frameSize, params	)
<VideoWriter object>	=	cv.VideoWriter(	filename, apiPreference, fourcc, fps, frameSize, params	)

```

* filename 存储的视频名
* fourcc意为四字符代码（Four-Character Codes），顾名思义，该编码由四个字符组成,下面是VideoWriter_fourcc对象一些常用的参数，注意：字符顺序不能弄混
  * cv2.VideoWriter_fourcc('I', '4', '2', '0'),该参数是YUV编码类型，文件名后缀为.avi
  * cv2.VideoWriter_fourcc('P', 'I', 'M', 'I'),该参数是MPEG-1编码类型，文件名后缀为.avi
  * cv2.VideoWriter_fourcc('X', 'V', 'I', 'D'),该参数是MPEG-4编码类型，文件名后缀为.avi
  * cv2.VideoWriter_fourcc('T', 'H', 'E', 'O'),该参数是Ogg Vorbis,文件名后缀为.ogv
  * cv2.VideoWriter_fourcc('F', 'L', 'V', '1'),该参数是Flash视频，文件名后缀为.flv
* fps 存储的视频帧速率
* frameSize 存储视频的每一帧大小
* isColor 默认为存储的为多通道视频(彩色)，定义为0时输出灰色视频

#### Tips:

>

cv.VideoWriter_fourcc（'M'，'J'，'P'，'G'）
也可以写成成
fourcc = cv.VideoWriter_fourcc（*'MJPG')

> * 在Fedora中：DIVX，XVID，MJPG，X264，WMV1，WMV2。（最好使用XVID。MJPG会生成大尺寸的视频。X264会生成非常小的尺寸的视频）
> * 在Windows中：DIVX（尚待测试和添加）
> * 在OSX中：MJPG（.mp4），DIVX（.avi），X264（.mkv）。

> 当 fourcc=-1 系统会跳出对话框让你选择编码方式

> 将视频转化为图像序列首先确保图片的名称顺序(eg. img_%02d.jpg) 并设置 fourcc=0 或者是 fps=0.

> 使用未压缩的图像格式去保存视频原始帧数 (eg. img_%02d.BMP)

> 大多数视频编码都是有损的，可以使用以下无损格式输出你的无损视频 (eg. FFMPEG FFV1, Huffman HFYU, Lagarith LAGS, etc...)
> 如果 FFMPEG可用, 设置 codec=0; fps=0; 可以获得未压缩的原始视频.
