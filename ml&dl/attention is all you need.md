transformer architecture.
![[Pasted image 20250203144447.png]]
[paper](https://arxiv.org/abs/1706.03762)
![[Pasted image 20250203150749.png]]
$$
Attention(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V
$$
T means transpose here

Positional Encoding:
$$
PE_{(pos, 2i)} = \sin\left(\frac{pos}{10000^{2i/d_{\text{model}}}}\right)
$$

$$
PE_{(pos, 2i+1)} = \cos\left(\frac{pos}{10000^{2i/d_{\text{model}}}}\right)
$$
just make input to be "different" where pos is the position and i is the dimension. $d_{\text{model}}$ means the dimension size