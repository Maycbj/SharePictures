# fast-style-transfer

## 项目地址
[论文地址](https://arxiv.org/abs/1508.06576)
[代码地址](https://github.com/lengstrom/fast-style-transfer#stylizing-video)

## 项目介绍
Add styles from famous paintings to any photo in a fraction of a second! [You can even style videos!](#video-stylization)

Our implementation is based off of a combination of Gatys' [A Neural Algorithm of Artistic Style](https://arxiv.org/abs/1508.06576), Johnson's [Perceptual Losses for Real-Time Style Transfer and Super-Resolution](http://cs.stanford.edu/people/jcjohns/eccv16/), and Ulyanov's [Instance Normalization](https://arxiv.org/abs/1607.08022). 


## fine-tuning模型链接:
* VGG19:    [https://gist.github.com/ksimonyan/3785162f95cd2d5fee77](https://gist.github.com/ksimonyan/3785162f95cd2d5fee77)
* MobileNet:    [https://github.com/shicai/MobileNet-Caffe](https://github.com/shicai/MobileNet-Caffe)
* ResNet:   [https://github.com/KaimingHe/deep-residual-networks](https://github.com/KaimingHe/deep-residual-networks)

## 学习曲线比对(前65000次迭代)
<table>
    <tr>
        <th>VggNet(baseline)</th>
        <td><img src="https://raw.githubusercontent.com/Maycbj/Share/intern_sina/Realtime_MultiPerson_Pose_Estimation/vgg.png" width=100% height=50%></td>
    </tr>
    <tr>
        <th>MobileNet </th>
        <td><img src="https://raw.githubusercontent.com/Maycbj/Share/intern_sina/Realtime_MultiPerson_Pose_Estimation/mobile.png" width=100% height=50%></td>
    </tr>
    <tr>
        <th>ResNet</th>
        <td><img src="https://raw.githubusercontent.com/Maycbj/Share/intern_sina/Realtime_MultiPerson_Pose_Estimation/resnet.png" width=100% height=50%></td>
    </tr>
</table>


## 预处理验证:
(1) VGG: 零均值 + 归一化, 在ImageNet上效果较好。
![VggNet](https://raw.githubusercontent.com/Maycbj/Share/intern_sina/Realtime_MultiPerson_Pose_Estimation/vgg1.png)

(2) ResNet:减mean_file,不用scale,(归一化则分类错误)分类结果比VGG要好。
![ResNet](https://raw.githubusercontent.com/Maycbj/Share/intern_sina/Realtime_MultiPerson_Pose_Estimation/resnet1.png)

## 最终效果比对
最后200次迭代，同样大小的图片(224*224)

* Loss及耗时比对
<table>
    <tr>
        <th></th>
        <th>loss</th>
        <th>耗时(前向传播时间)</th>
    </tr>
    <tr>
        <th>VGG19</th>
        <td>183</td>
        <td>26ms</td>
    </tr>
        <th>MobileNet</th>
        <td>199</td>
        <td>16ms</td>
    </tr>
        <th>ResNet</th>
        <td>182</td>
        <td>21ms</td>
    </tr>
    </tr>
        <th>最终优化ResNet</th>
        <td>182</td>
        <td>17ms</td>
    </tr>
</table>
* 结果图比对
<table>
  <tr>
    <th>ModelName</th>
    <th>StyleImage</th>
    <th>ResultImage</th>
</tr>
<tr>
    <td>wave</td>
    <td><img src="https://raw.githubusercontent.com/Maycbj/Share/intern_sina/Realtime_MultiPerson_Pose_Estimation/mobile2.png" width=100% height=70%></td>
    <td><img src="https://raw.githubusercontent.com/Maycbj/Share/intern_sina/Realtime_MultiPerson_Pose_Estimation/resnet2.png" width=100% height=70%></td>
</tr>
<tr>
    <td>mountains</td>
    <td><img src="https://raw.githubusercontent.com/Maycbj/Share/intern_sina/Realtime_MultiPerson_Pose_Estimation/mobile3.png" width=100% height=70%></td>
    <td><img src="https://raw.githubusercontent.com/Maycbj/Share/intern_sina/Realtime_MultiPerson_Pose_Estimation/resnet3.png" width=100% height=70%></td>
</tr>
<tr>
    <td><img src="https://raw.githubusercontent.com/Maycbj/Share/intern_sina/Realtime_MultiPerson_Pose_Estimation/vgg4.png" width=100% height=70%></td>
    <td><img src="https://raw.githubusercontent.com/Maycbj/Share/intern_sina/Realtime_MultiPerson_Pose_Estimation/mobile4.png" width=100% height=70%></td>
    <td><img src="https://raw.githubusercontent.com/Maycbj/Share/intern_sina/Realtime_MultiPerson_Pose_Estimation/resnet4.png" width=100% height=70%></td>
</tr>
</table>

##摄像头远程连接使用
* 1、获取远程连接代码
<pre>
git clone https://github.com/Maycbj/Share.git -b intern_sina`
</pre>
* 2、修改mac的ip地址 
<pre>
cd Share/internship/sina/Realtime_MultiPerson_Pose_Estimation/trans
vim receive.py 
address = ('10.236.10.44', 8003) -->  address = ('mac.de.i.p', 8003)
</pre>


* 3、登陆远程服务器：
<pre>
ssh root@10.85.125.105
cd /disk/data0/users/mayuchen/Project/Realtime_Multi-Person_Pose_Estimation/testing/python
vim server.py 
address_s = ('10.236.10.44', 8003) -->  address = ('mac.de.i.p', 8003)
</pre>

* 4、运行程序
<pre>
//本机上运行
sh run.sh
//立即在linux上运行
python server.py v
</pre>







