#### Fully-Convolutional Siamese Networks for Object Tracking
###### Luca Bertinetto, Jack Valmadre, João F. Henriques, Andrea Vedaldi, Philip H. S. Toor

@div[left]

__概要__<br>
対象動画から得られる学習データのみから、陽に見た目情報のモデルを学習していた従来手法は表現力に制限がある。一方で、深層学習ベースの手法は、追跡対象が事前に与えられないことから、オンラインでSGDを行う必要があり、十分な速度が出ないという問題がある。本論文では、One-Shot Learningなどにおいて画像パッチのペアの類似度を学習するSiamese Networkを物体追跡に応用する。物体検出用データセット（Object detection from video (ILSVRC2015)）でオフライン学習させるEnd-to-EndのFully-Convolution Siamese Network（SiamFC）を提案し、リアルタイム以上の速度とSOTAを実現した。<br>
<br>
__手法・新規性__<br>
見本画像$z$と探索画像$x$を比較する関数$f$は、特徴量抽出を行うCNN（`$\varphi$`）と特徴量の比較を行うCross-Correlation演算（`$\ast$`）を用いて以下のように記述される。<br>
`$$ f(z, x) = \varphi(z) \ast \varphi(x) + b \mathbb{1} $$`
FCNNによって見本画像$z$より大きい探索画像$x$を一気に探索可能であり、スケールを変えた探索画像をミニバッチにすることで一回の順伝搬でマルチスケール探索も可能になる。以下の最適化問題を解く。<br>
`$$ \mathop{\rm arg~min}\limits_{\theta} \mathbb{E} [L(y,f(z,x:\theta))] $$`
`$$ L(y,v) = \frac{1}{| \mathcal{D} |} \sum_{u \in \mathcal{D}} \log (1 + \exp y[u] v[u]) $$`
ただし、$v$は実数のスコア、$y \in {+1, -1}$は正解ラベルである。<br>

@divend


@div[right]

![SiameseFC](assets/img/Siamese-FC.png =full)
<br>

__リンク__<br>
・[論文](https://arxiv.org/pdf/1606.09549.pdf)<br>
・[プロジェクト](https://www.robots.ox.ac.uk/~luca/siamese-fc.html)<br>
・[GitHub](https://github.com/bertinetto/siamese-fc)<br>
・[発表動画](https://youtu.be/jZoUalMMZ_0)<br>
・[スライド１（VOT 2016）](http://data.votchallenge.net/vot2016/presentations/presentation_Bertinetto.pdf)<br>
・[スライド２](https://pdfs.semanticscholar.org/presentation/4c91/827cceb97183c4d48ca09e1c7587577c8d54.pdf)<br>

@divend