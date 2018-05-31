# FaceRecognition-tensorflow

运行环境
下面为软件的运行搭建系统环境。
系统: window或linux
软件: python 3.x 、 tensorflow
python支持库:
tensorflow:
pip install tensorflow #cpu版本
pip install rensorflow-gpu #gpu版本，需要cuda与cudnn的支持，不清楚的可以选择cpu版
numpy:
pip install numpy
opencv:
pip install opencv-python
dlib:
pip install dlib

获取本人图片集
获取本人照片的方式当然是拍照了，我们需要通过程序来给自己拍照，如果你自己有照片，也可以用那些现成的照片，但前提是你的照片足够多。这次用到的照片数是10000张，程序运行后，得坐在电脑面前不停得给自己的脸摆各种姿势，这样可以提高训练后识别自己的成功率，在程序中加入了随机改变对比度与亮度的模块，也是为了提高照片样本的多样性。
程序中使用的是dlib来识别人脸部分，也可以使用opencv来识别人脸，在实际使用过程中，dlib的识别效果比opencv的好，但opencv识别的速度会快很多，获取10000张人脸照片的情况下，dlib大约花费了1小时，而opencv的花费时间大概只有20分钟。opencv可能会识别一些奇怪的部分，所以综合考虑之后我使用了dlib来识别人脸。

get_my_faces.py

获取其他人脸图片集
需要收集一个其他人脸的图片集，只要不是自己的人脸都可以，可以在网上找到，这里我给出一个我用到的图片集
先将下载的图片集，解压到项目目录下的input_img目录下，也可以自己指定目录(修改代码中的input_dir变量)
接下来使用dlib来批量识别图片中的人脸部分，并保存到指定目录下

set_other_people.py

这个项目用到的图片数是10000张左右，如果是自己下载的图片集，控制一下图片的数量避免数量不足，或图片过多带来的内存不够与运行缓慢


训练模型
有了训练数据之后，通过cnn来训练数据，就可以让她记住我的人脸特征，学习怎么认识我了。
train_faces.py
训练之后的数据会保存在当前目录下。



使用模型进行识别

最后就是让她认识我了，很简单，只要运行程序，让摄像头拍到我的脸，她就可以轻松地识别出是不是我了。
is_my_face.py






自己脸识别:

![](https://github.com/ttanzhiqiang/FaceRecognition-tensorflow/blob/master/1.png)

图像识别:

![](https://github.com/ttanzhiqiang/FaceRecognition-tensorflow/blob/master/2.png)

别人的脸识别:

![](https://github.com/ttanzhiqiang/FaceRecognition-tensorflow/blob/master/3.png)
