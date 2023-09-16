##### 
```
cv2.cvtColor(src, code[, dst[, dstCn]])
```
- `src`：需要转换颜色空间的图像。
- `code`：颜色空间转换代码。
- `dst`（可选）：与源图像大小和深度相同的输出图像。
- `dstCn`（可选）：目标图像中的通道数。如果该参数为 0，则根据 `src` 和 `code` 自动推导通道数。

```
cv2.destoryAllWindows()
```
- 窗口保持打开：如果不调用`cv2.destroyAllWindows()`，OpenCV创建的窗口将保持打开状态，直到用户手动关闭它们或程序终止。
- 可能导致资源泄漏：不关闭窗口可能会导致资源泄漏，特别是在循环中使用`cv2.imshow()`时，每次迭代都会创建新窗口，而不关闭旧窗口。

```
cv2.imwrite(filename, image)
```
- `filename`可以指明路径，如果该路径不存在，则创建。

```
cv2.imread(filename, image)
```
`filename`为读出图片的名字 。

```
cv2.IMREAD_COLOR
cv2.IMREAD_GRAYSCALE
cv2.IMREAD_ANYCOLOR
cv2.IMREAD_UNCHANGED
cv2.IMREAD_ANYDEPTH
cv2.IMREAD_ANYDEPTH|cv2.IMREAD_COLOR
cv2.IMREAD_REDUCED_GRAYSCALE_2
cv2.IMREAD_REDUCED_COLOR_2
cv2.IMREAD_REDUCED_GRAYSCALE_4
cv2.IMREAD_REDUCED_COLOR_4
cv2.IMREAD_REDUCED_GRAYSCALE_8
cv2.IMREAD_REDUCED_COLOR_8
```
- `cv2.IMREAD_COLOR`：以彩色模式加载图像。这是默认选项，为每个通道提供 3 通道 BGR 图像，每个图像具有 8 位值（0-255）。
- `cv2.IMREAD_GRAYSCALE`：以灰度模式加载图像。这提供了一个 8 位灰度图像。
- `cv2.IMREAD_ANYCOLOR`：尝试加载图像，但不关心颜色格式，如果图象是彩色的，它将以彩色模式加载，否则以灰度模式加载。根据文件中的元数据，它提供每通道 8 位的 BGR 图像或 8 位的灰度图像。
- `cv2.IMREAD_UNCHANGED`：加载图像，包括[[杂项#^025801|图像的阿尔法通道]]，不进行任何修改。读取所有图像数据，包括 alpha 或透明通道（如果有）作为第四通道。
- `cv2.IMREAD_ANYDEPTH`：尝试加载图像，不关心位深度，图像的位深度是指每个像素的颜色通道的位数。这将以原始位深度加载灰度图像。 例如，如果文件表示此格式的图像，它将提供每通道 16 位的灰度图像。
- `cv2.IMREAD_ANYDEPTH | cv2.IMREAD_COLOR`：尝试加载图像，不关心位深度，以彩色模式加载。此组合以原始位深度加载 BGR 颜色的图像。
- `cv2.IMREAD_REDUCED_GRAYSCALE_2`：这会以原始分辨率的一半加载灰度图像。 例如，如果文件包含`640 x 480`的图像，则它将作为`640 x 480`的图像加载。
- `cv2.IMREAD_REDUCED_COLOR_2`：这将以每通道 8 位 BGR 的颜色加载图像，其分辨率为原始分辨率的一半。
- `cv2.IMREAD_REDUCED_GRAYSCALE_4`：这会以原始分辨率的四分之一加载灰度图像。
- `cv2.IMREAD_REDUCED_COLOR_4`：这将以每通道 8 位的颜色加载原始分辨率的四分之一的图像。
- `cv2.IMREAD_REDUCED_GRAYSCALE_8`：这会以原始分辨率的八分之一以灰度加载图像。
- `cv2.IMREAD_REDUCED_COLOR_8`：这将以每通道 8 位的颜色加载图像，其分辨率为原始分辨率的八分之一。
以不同的降采样级别加载图像。这些常量用于加载具有不同降采样级别的图像。数字表示降采样的级别，例如，"2"表示图像宽度和高度减小到原始大小的1/2。
##### 下载
```
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple opencv-python
```
##### 灰度图
```
import cv2  
  
image = cv2.imread("opencv_logo.jpg")  
  
cv2.imshow("blue", image[:, :, 0])  
cv2.imshow("green", image[:, :, 1])  
cv2.imshow("red", image[:, :, 2])  
  
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)  
cv2.imshow("gray", gray)  
  
cv2.waitKey()
```
##### 图像的裁剪
```
import cv2  
  
image = cv2.imread("opencv_logo.jpg")  
  
crop = image[10:170, 40:200]  
  
cv2.imshow("crop", crop)  
cv2.waitKey()
```
##### 画图
```
import cv2  
import numpy as np  
  
image = np.zeros([300, 300, 3], dtype=np.uint8)  
  
cv2.line(image, (100, 200), (250, 250), (255, 255, 0), 2)  
cv2.rectangle(image, (30, 100), (60, 150), (0, 255, 255), 4)  
cv2.circle(image, (150, 100), 20, (255, 0, 255), 5)  
cv2.putText(image, "hello", (100, 50), 0, 1, (255, 255, 255), 1)  
  
cv2.imshow("image", image)  
cv2.waitKey()
```
##### 噪点去除
```
import cv2  
  
image = cv2.imread("plane.jpg")  
  
gauss = cv2.GaussianBlur(image, (5, 5), 0)  
median = cv2.medianBlur(image, 5)  
  
cv2.imshow("image", image)  
cv2.imshow("gauss", gauss)  
cv2.imshow("median", median)  
  
cv2.waitKey()
```
##### 获取转角
```
import cv2  
  
image = cv2.imread("opencv_logo.jpg")  
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)  
  
corners = cv2.goodFeaturesToTrack(gray, 500, 0.1, 10)  
for corner in corners:  
    x, y = corner.ravel()  
    cv2.circle(image, (int(x), int(y)), 3, (255, 0, 255), -1)  
  
cv2.imshow("corners", image)  
cv2.waitKey()
```
##### 匹配菱形框
```
import cv2  
import numpy as np  
  
image = cv2.imread("poker.jpg")  
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)  
  
template = gray[75:105, 235:265]  
  
match = cv2.matchTemplate(gray, template, cv2.TM_CCOEFF_NORMED)  
location = np.where(match >= 0.9)  
  
w, h = template.shape[0:2]  
for p in zip(*location[::-1]):  
    x1, y1 = p[0], p[1]  
    x2, y2 = x1 + w, y1 + h  
    cv2.rectangle(image, (x1, y1), (x2, y2), (0, 255, 0), 2)  
  
cv2.imshow("image", image)  
cv2.waitKey()
```
##### 图像明暗变化梯度图
```
import cv2  
  
gray = cv2.imread("opencv_logo.jpg", cv2.IMREAD_GRAYSCALE)  
  
laplacian = cv2.Laplacian(gray, cv2.CV_64F)  
canny = cv2.Canny(gray, 100, 200)  
  
cv2.imshow("gray", gray)  
cv2.imshow("laplacian", laplacian)  
cv2.imshow("canny", canny)  
  
cv2.waitKey()
```

##### 阈值处理
```
import cv2  
  
gray = cv2.imread("bookpage.jpg", cv2.IMREAD_GRAYSCALE)  
ret, binary = cv2.threshold(gray, 10, 255, cv2.THRESH_BINARY)  
binary_adaptive = cv2.adaptiveThreshold(  
    gray, 255, cv2.ADAPTIVE_THRESH_MEAN_C, cv2.THRESH_BINARY, 155, 1)  
ret1, binary_otsu = cv2.threshold(gray, 0 ,255, cv2.THRESH_BINARY + cv2.THRESH_OTSU)  
  
cv2.imshow("gray", gray)  
cv2.imshow("binary", binary)  
cv2.imshow("adaptive", binary_adaptive)  
cv2.imshow("otsu", binary_otsu)  
  
cv2.waitKey()
```
##### 形态学算法（腐蚀、膨胀）
```
import cv2  
import numpy as np  
  
gray = cv2.imread("opencv_logo.jpg", cv2.IMREAD_GRAYSCALE)  
  
_, binary = cv2.threshold(gray, 200, 255, cv2. THRESH_BINARY_INV)  
kernel = np.ones((5, 5), np.uint8)  
  
erosion = cv2.erode(binary, kernel)  
dilation = cv2.dilate(binary, kernel)  
  
cv2.imshow("binary", binary)  
cv2.imshow("erosion", erosion)  
cv2.imshow("dilation", dilation)  
  
cv2.waitKey()
```
##### 使用`numpy.array`访问图像数据并显示图像
```
import cv2  
  
img = cv2.imread('MyPic.png')  
img[150, 120] = [255, 255, 255]  
  
cv2.imshow('1', img)  
cv2.waitKey()
```
- 操作 BGR 图像中坐标`(150, 120)`处的像素并将其变成白色像素，

```
import cv2  
  
img = cv2.imread('MyPic.png')  
  
cv2.imshow('1', img)  
  
img.itemset((150, 120, 0), 255)    
print(img.item(150, 120, 0))    
  
cv2.imshow('2', img)
cv2.waitKey()
```
- 更改特定像素的蓝色值，例如坐标`(150, 120)`处的像素。 `numpy.array`类型提供了一种方便的方法`item`，它采用三个参数：`x`（或左侧）位置，`y`（或顶部）位置以及索引 （`x`，`y`）位置处的数组内（请记住，在 BGR 图像中，特定位置的数据是包含 B，G 和 R 值按此顺序排列），并在索引位置返回该值。 另一种方法`itemset`将特定像素的特定通道的值设置为指定值。 `itemset`接受两个参数：一个三元素元组（`x`，`y`和索引）和新值。

``` 
import cv2  
  
img = cv2.imread('MyPic.png')  
img[:, :, 1] = 0  
  
cv2.imshow('1', img)  
cv2.waitKey()
```
- 它基本上指示程序从所有行和列中获取所有像素，并将绿色值（三元素 BGR 数组的索引之一）设置为`0`。 如果显示此图像，您会注意到完全没有绿色。

```
import cv2  
  
img = cv2.imread('MyPic.png')  
  
cv2.imshow('1', img)  
  
my_roi = img[0:100, 0:100]  
img[300:400, 300:400] = my_roi  
  
cv2.imshow('2', img)  
cv2.waitKey()
```
- 我们可以通过使用 NumPy 的数组切片访问原始像素来做几件有趣的事情。 其中之一是定义**兴趣区域**（**ROI**）。 定义区域后，我们可以执行许多操作。 例如，我们可以将此区域绑定到变量，定义第二个区域，并将第一个区域的值分配给第二个区域（因此，将图像的一部分复制到图像中的另一个位置）

```
import cv2  
  
img = cv2.imread('MyPic.png')  
print(img.shape)  
print(img.size)  
print(img.dtype)
```
- `shape`：这是一个描述数组形状的元组。 对于图像，它包含（按顺序）高度，宽度和（如果图像是彩色的）通道数。 `shape`元组的长度是确定图像是灰度还是彩色的有用方法。 对于灰度图像，我们有`len(shape) == 2`，对于彩色图像，我们有`len(shape) == 3`。
- `size`：这是数组中元素的数量。 在灰度图像的情况下，这与像素数相同。 在 BGR 图像的情况下，它是像素数的三倍，因为每个像素都由三个元素（B，G 和 R）表示。
- `dtype`：这是数组元素的数据类型。 对于每通道 8 位图像，数据类型为`numpy.uint8`。
##### 读/写视频文件
```
import cv2  
  
videoCapture = cv2.VideoCapture('MyInputVid.mp4')  
fps = videoCapture.get(cv2.CAP_PROP_FPS)  
size = (int(videoCapture.get(cv2.CAP_PROP_FRAME_WIDTH)),  
        int(videoCapture.get(cv2.CAP_PROP_FRAME_HEIGHT)))  
videoWriter = cv2.VideoWriter(  
    'MyOutputVid.mp4', cv2.VideoWriter_fourcc(*'mp4v'),  
    fps, size)  
  
success, frame = videoCapture.read()  
while success:  # Loop until there are no more frames.  
    videoWriter.write(frame)  
    success, frame = videoCapture.read()  
  
videoCapture.release()  
videoWriter.release()  
cv2.destroyAllWindows()

# 参考书代码
import cv2
videoCapture = cv2.VideoCapture('MyInputVid.avi')
fps = videoCapture.get(cv2.CAP_PROP_FPS)
size = (int(videoCapture.get(cv2.CAP_PROP_FRAME_WIDTH)),
        int(videoCapture.get(cv2.CAP_PROP_FRAME_HEIGHT)))
videoWriter = cv2.VideoWriter(
    'MyOutputVid.avi', cv2.VideoWriter_fourcc('I','4','2','0'),
    fps, size)
success, frame = videoCapture.read()
while success:  # Loop until there are no more frames.
    videoWriter.write(frame)
    success, frame = videoCapture.read()
```
- **注意**参考书中适用的视频格式为`avi`，我将代码略加修改，适配了更常见的`mp4`格式。
- `VideoWriter`类的构造器的参数值得特别注意。 必须指定视频的文件名。 具有该名称的任何先前存在的文件都将被覆盖。 还必须指定视频编解码器。 可用的编解码器可能因系统而异。 支持的选项可能包括以下内容：
	1. `0`：此选项是未压缩的原始视频文件。 文件扩展名应为`.avi`。
	2. `cv2.VideoWriter_fourcc('I','4','2','0')`：此选项是未压缩的 YUV 编码，4:2:0 色度被二次采样。 这种编码具有广泛的兼容性，但会产生大文件。 文件扩展名应为`.avi`。
	3. `cv2.VideoWriter_fourcc('P','I','M','1')`：此选项是 MPEG-1。 文件扩展名应为`.avi`。
	4. `cv2.VideoWriter_fourcc('X','V','I','D')`：此选项是相对较旧的 MPEG-4 编码。 如果要限制生成的视频的大小，这是一个不错的选择。 文件扩展名应为`.avi`。
	5. `cv2.VideoWriter_fourcc('M','P','4','V')`：此选项是另一种相对较旧的 MPEG-4 编码。 如果要限制生成的视频的大小，这是一个不错的选择。 文件扩展名应为`.mp4`。
	6. `cv2.VideoWriter_fourcc('X','2','6','4')`：此选项是相对较新的 MPEG-4 编码。 如果您想限制最终视频的大小，这可能是最好的选择。 文件扩展名应为`.mp4`。
	7. `cv2.VideoWriter_fourcc('T','H','E','O')`：此选项为 **Ogg Vorbis**。 文件扩展名应为`.ogv`。
	8. `cv2.VideoWriter_fourcc('F','L','V','1')`：此选项是 Flash 视频。 文件扩展名应为`.flv`。
- 但仍可能会遇见一些问题吗，下面是一些解决方案：
	1. **重新编译OpenCV**：如果使用的是自定义构建的OpenCV，尝试重新编译OpenCV时确保启用了FFmpeg支持。在CMake配置时，启用相应的选项，以便OpenCV可以使用FFmpeg。然后重新构建OpenCV。
	2. **使用不同的FourCC代码**：尝试使用其他编解码器
	3. **下载并安装对应的库** 
	4. **检查OpenCV版本**：如果 OpenCV 版本较旧，可能会存在问题。尝试更新到最新版本的 OpenCV，以获得更好的支持。
- 还必须指定帧速率和帧大小。 由于我们正在从另一个视频复制，因此可以从`VideoCapture`类的`get`方法读取这些属性。
##### 捕捉相机帧并输出相机
```
import cv2  
  
cameraCapture = cv2.VideoCapture(0)  
fps = 30  # An assumption  
size = (int(cameraCapture.get(cv2.CAP_PROP_FRAME_WIDTH)),  
        int(cameraCapture.get(cv2.CAP_PROP_FRAME_HEIGHT)))  
videoWriter = cv2.VideoWriter(  
    'MyOutputVid.avi', cv2.VideoWriter_fourcc('I','4','2','0'),  
    fps, size)  
  
success, frame = cameraCapture.read()  
numFramesRemaining = 10 * fps - 1 # 10 seconds of frames  
while success and numFramesRemaining > 0:  
    videoWriter.write(frame)  
    success, frame = cameraCapture.read()  
    numFramesRemaining -= 1
    
cameraCapture.release()
```
##### 在窗口中显示摄像机帧
```
import cv2  
  
capture = cv2.VideoCapture(0)  
  
while True:  
    ret, frame = capture.read()  
    cv2.imshow("camera", frame)  
    key = cv2.waitKey(1)  
    if key != -1:  
        break  
  
capture.release()
```
- `capture.read()` 是 OpenCV 中用于从视频捕获设备（例如摄像头）中读取一帧视频的函数。它返回两个值，第一个是布尔值（通常命名为 `ret`），表示是否成功读取帧，第二个是视频帧本身，通常是一个NumPy数组。
- `cv2.VideoCapture()` 是 OpenCV 中用于创建视频捕获对象的函数，可以用于从摄像头、视频文件或其他视频源中捕获视频帧。它接受一个参数，该参数可以是以下三种类型之一：
	1. 整数（通常为0、1、2等）：表示要使用的摄像头的索引。通常情况下，0表示默认摄像头，1表示第二个摄像头（如果有多个摄像头）。
	```
	import cv2
	# 创建一个视频捕获对象，0表示默认摄像头
	capture = cv2.VideoCapture(0)
	```
	1. 字符串：表示视频文件的路径，可以是本地文件路径或网络视频流的URL。
	2. IP摄像头地址：如果您有网络摄像头，可以将其IP地址作为字符串传递给 `cv2.VideoCapture()`，以便从网络摄像头捕获视频。

```
import cv2

clicked = False
def onMouse(event, x, y, flags, param):
    global clicked
    if event == cv2.EVENT_LBUTTONUP:
        clicked = True

cameraCapture = cv2.VideoCapture(0)

cv2.namedWindow('MyWindow')
cv2.setMouseCallback('MyWindow', onMouse)

print('Showing camera feed. Click window or press any key to stop.')
success, frame = cameraCapture.read()
while success and cv2.waitKey(1) == -1 and not clicked:
    cv2.imshow('MyWindow', frame)
    success, frame = cameraCapture.read()
 
cv2.destroyWindow('MyWindow')
cameraCapture.release()
```
- `def onMouse(event, x, y, flags, param)`: 定义一个鼠标事件处理函数`onMouse`，该函数会在鼠标事件发生时被调用。它接受五个参数：`event`表示触发的事件类型，`x`和`y`表示鼠标事件发生的坐标，`flags`表示鼠标事件的附加标志，`param`表示可选参数。
	1. 在`onMouse`函数中，当鼠标左键被释放（`cv2.EVENT_LBUTTONUP`事件）时，将全局变量`clicked`设置为True，表示用户点击了窗口。
	2. `event`参数表示触发的鼠标事件类型。在这个函数中，我们检查是否是左键释放事件 (`cv2.EVENT_LBUTTONUP`)。
	3. `x`和`y`参数表示鼠标事件发生的坐标，即鼠标指针在窗口上的位置。
	4. `flags`参数包含了与事件相关的附加标志，但在这个代码中没有使用。
	5. `param`参数是可选参数，通常用于传递额外的数据，但在这个代码中也没有使用。
- `cv2.namedWindow('MyWindow')`: 创建一个名为"MyWindow"的窗口，用于显示摄像头捕获的视频。
	1. `cv2.namedWindow()` 是OpenCV库中的一个函数，用于创建一个窗口以显示图像、视频或其他视觉数据。它的一般语法如下：`cv2.namedWindow(winname, flags=cv2.WINDOW_AUTOSIZE)
	2. `winname`: 表示要创建的窗口的名称或标识符。您可以自定义窗口的名称，以便在后续的操作中引用该窗口。
	3. `flags`（可选参数）: 指定窗口的标志。这是一个可选参数，默认值为`cv2.WINDOW_AUTOSIZE`，表示窗口的大小会自动根据显示内容调整。您也可以将其设置为`cv2.WINDOW_NORMAL`，以允许手动调整窗口大小。
- `cv2.setMouseCallback('MyWindow', onMouse)`: 在窗口"MyWindow"上设置鼠标事件回调函数，以便捕获鼠标事件。
	1. `cv2.setMouseCallback()` 是OpenCV中的一个函数，用于设置鼠标事件的回调函数，以便在指定的窗口上捕获和处理鼠标事件。它的一般语法如下：`cv2.setMouseCallback(windowName, onMouse, param=None)`
	2. `windowName`: 表示要在其上设置鼠标事件回调的窗口的名称。通常，您在使用`cv2.namedWindow()`创建窗口时指定的窗口名称。
	3. `onMouse`: 是一个回调函数，用于处理鼠标事件。当鼠标事件发生时，OpenCV将调用此函数并传递相关的事件信息。
- 回调的事件参数是以下操作之一：
	- `cv2.EVENT_MOUSEMOVE`：此事件涉及鼠标移动。
	- `cv2.EVENT_LBUTTONDOWN`：此事件是指按下左按钮时会使其按下。
	- `cv2.EVENT_RBUTTONDOWN`：此事件是指按下该按钮时向下的右键。
	- `cv2.EVENT_MBUTTONDOWN`：此事件是指按下中键时按下的中键。
	- `cv2.EVENT_LBUTTONUP`：此事件是指释放时返回的左按钮。
	- `cv2.EVENT_RBUTTONUP`：此事件指的是释放按钮时再次弹出的右键。
	- `cv2.EVENT_MBUTTONUP`：此事件是指释放按钮时中间按钮再次出现。
	- `cv2.EVENT_LBUTTONDBLCLK`：此事件表示双击左按钮。
	- `cv2.EVENT_RBUTTONDBLCLK`：此事件表示双击右键。
	- `cv2.EVENT_MBUTTONDBLCLK`：此事件是指双击中间按钮。
- 鼠标回调的`flags`参数可能是以下事件的按位组合：
	- `cv2.EVENT_FLAG_LBUTTON`：此事件是指按下左按钮。
	- `cv2.EVENT_FLAG_RBUTTON`：此事件表示按下了右键。
	- `cv2.EVENT_FLAG_MBUTTON`：此事件是指按下中间按钮。
	- `cv2.EVENT_FLAG_CTRLKEY`：此事件是指按下`Ctrl`键。
	- `cv2.EVENT_FLAG_SHIFTKEY`：此事件是指按下`Shift`键。
	- `cv2.EVENT_FLAG_ALTKEY`：此事件是指按下`Alt`键。
##### 
##### 
##### 
##### 
##### 
##### 
##### 
##### 
##### 