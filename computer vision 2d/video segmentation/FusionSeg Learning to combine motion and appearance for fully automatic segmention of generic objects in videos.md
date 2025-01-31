
## comments
using a CNN network to solve this task, using RGB and optical flow as input.
use pretrained model to segment 。。。。。
it is hard to say if it is unsupervised segmentation。。。
![[Pasted image 20250131115207.png]]

[paper](https://arxiv.org/pdf/1701.05384)
## abstract
We propose an end-to-end learning framework for seg menting generic objects in videos. Our method learns to combine appearance and motion information to produce pixel level segmentation masks for all prominent objects. We formulate the task as a structured prediction problem and design a two-stream fully convolutional neural net work which fuses together motion and appearance in a unified framework. Since large-scale video datasets with pixel level segmentations are lacking, we show how to boot strap weakly annotated videos together with existing im age recognition datasets for training. Through experiments on three challenging video segmentation benchmarks, our method substantially improves the state-of-the-art results for segmenting generic (unseen) objects. Code and pre trained models are available on the project website