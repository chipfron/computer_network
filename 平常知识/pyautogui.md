##### 屏幕的分辨率
```
import pyautogui  

width, height = pyautogui.size()  
x, y = pyautogui.position()    
result = pyautogui.onScreen(2000, 2222) 

print(f"宽度：{width}, 高度：{height}")
print(f"{x}, {y}")
print(f"{result}")
```
其中`print(f"宽度：{width}, 高度：{height}")`中的`f`将`width`和`height`替换成了获取的值，可以将其当成`%s`的作用。详情见[f字符串](https://realpython.com/python-f-strings/)
##### 鼠标的移动
```
import pyautogui  
  
pyautogui.moveTo(800, 800, duration=2)  
pyautogui.move(0, -200, duration=0.1)  
pyautogui.move(-200, 0)
```
`duration`表示移动持续的时间，不设置`duration`则默认为0.1。
##### 拖动鼠标
```
import pyautogui  
  
pyautogui.moveTo(700, 530, duration=2)  
pyautogui.dragTo(1, 1, button='left', duration=2)  
pyautogui.drag(100, 400, button='right', duration=2)
```
`dragTo`是拖动到某个点，`drag`是向某个方向拖动多少像素。
##### 鼠标的点击
```
import pyautogui  
  
x, y = pyautogui.position()  
  
pyautogui.click(button='left')  
pyautogui.click(x, y, button='left', clicks=2, interval=0.1, duration=2)  
pyautogui.doubleClick(x, y, button='left')  
pyautogui.tripleClick(x, y, button='left')
```
##### 鼠标的按压和释放
```
import pyautogui  
  
pyautogui.click(328, 190)  
pyautogui.moveTo(220, 480)  
pyautogui.mouseDown(button='left')  
pyautogui.move(500, 0)  
pyautogui.mouseUp(button='left')
```
##### 鼠标的滚动``
```
import pyautogui  
  
pyautogui.moveTo(220, 480)  
pyautogui.scroll(-10)
```
##### 键盘的输入
```
import pyautogui  
  
pyautogui.click(960, 460)  
pyautogui.write('This is a test!', interval=0.5)  
This is a test!
```
##### 键盘的按压
```
import pyautogui  
  
pyautogui.press('x')  
pyautogui.press('crtl')  
pyautogui.hotkey('ctrl', 'v')  
  
pyautogui.keyDown('crtl')  
pyautogui.keyUp('ctrl')
```
##### 
##### 