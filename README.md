# VoIP-Stega

Tools for VoIP steganography and steganalysis.

该工具可以用于VoIP语音隐写，包含两种隐写算法，CNV-QIM [1] 和 Pitch modulation [2]。同时该工具也用于构建第一届全国信息隐藏大赛（CIHC2019）音频组训练集。

使用方法如下：
1. 使用wav2pcm.py去掉wav文件头，将wav文件变成pcm文件，需要修改.py文件中wav文件的路径和pcm的保存路径。
2. 使用StegCoder.exe进行隐写
（1）将需要隐写的pcm文件放在一个命名为input的文件夹内
（2）新建一个output文件夹，用于存放隐写后的文件
（3）如果使用CNV-QIM隐写，隐写嵌入率为100%，则在命令提示符内输入 
StegCoder.exe -i input -o output -a cnv -r 100
如果使用基音隐写方法，隐写嵌入率为100%，则在命令提示符内输入 
StegCoder.exe -i input -o output -a pitch -r 100

注1：wav文件为8000HZ采样，16bit量化。
注2：输入和输出文件夹的名字可以自己指定，注意两种隐写数据不要指定在同一个输出文件夹下，可能会出现相同文件名而互相覆盖的问题。


若您在学术研究中用到该隐写工具，请引用如下论文：

【1】Xiao B, Huang Y, Tang S. An approach to information hiding in low bit-rate speech stream[C]//IEEE GLOBECOM 2008-2008 IEEE Global Telecommunications Conference. IEEE, 2008: 1-5.

【2】Huang Y, Liu C, Tang S, et al. Steganography integration into a low-bit rate speech codec[J]. IEEE transactions on information forensics and security, 2012, 7(6): 1865-1875.

===========================================================================================

根据上述 VoIP 隐写算法，我们构建了一个 VoIP 隐写分析数据集。

下载路径：Google Driver：【https://drive.google.com/open?id=1bjqlB4QjoLlB6yIvAQJ3ZjvU6IRX8Lpk】
          百度云盘：  链接：https://pan.baidu.com/s/16yiyOf1qZGUw2nZwyU_FgQ                  提取码：cfsa 

下载的压缩包中同时包含两段参考代码，可用于 提取G729a编码的语音信号中的LPC和PD特征，代码及说明包含在压缩文件中。

音频来源：采集不同人的语音信号，然后按照G.729a标准进行编码；

音频时长：编码后的语音信号统一裁剪成1s的语音片段；

	训练集：

	音频数量：隐写和非隐写音频各155327段。隐写和非隐写音频由相同的wav音频（约43个小时的中文音频）编码得到。
	文件夹：
  
		./ch_0_g729a：没有隐写的G.729a编码后音频
    
		./ch_steg_g729a：有隐写的G.729a编码后音频。
    
	测试集：

	2000段编码后时长为1s的音频片段，以0.5的概率选择数据集中的音频片段，然后随机挑选两种嵌入算法之一，并将随机生成的比特流以随机的嵌入率进行随机嵌入。


针对上述VoIP隐写算法的分析算法，可以参考如下相关研究工作：

【3】Huang Y F, Tang S, Zhang Y. Detection of covert voice-over Internet protocol communications using sliding window-based steganalysis[J]. IET communications, 2011, 5(7): 929-936.

【4】Lin Z, Huang Y, Wang J. RNN-SM: Fast steganalysis of VoIP streams using recurrent neural network[J]. IEEE Transactions on Information Forensics and Security, 2018, 13(7): 1854-1868.

【5】Yang Z, Yang H, Hu Y, et al. Real-Time Steganalysis for Stream Media Based on Multi-channel Convolutional Sliding Windows[J]. arXiv preprint arXiv:1902.01286, 2019.

【6】Yang H, Yang Z, Huang Y. Steganalysis of VoIP Streams with CNN-LSTM Network[C]//Proceedings of the ACM Workshop on Information Hiding and Multimedia Security. ACM, 2019: 204-209.
