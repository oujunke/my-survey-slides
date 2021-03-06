#### High-Speed Tracking with Kernelized Correlation Filters
###### João F. Henriques, Rui Caseiro, Pedro Martins, Jorge Batista

@div[left]

__概要__<br>
MOSSEは高速かつ高精度な物体追跡手法である。本論文では、カーネルリッジ回帰と巡回行列の性質を用いて、MOSSEをより一般化させたKernelized Correlation Filters（KCF）を提案する。KCFは非線形カーネルを選択することで、カーネルトリックにより、高精度な分類が可能となる。<br>
<br>
__手法・新規性__<br>
カーネルリッジ回帰の一般解はカーネル行列`$K \; (K_{ij} = \kappa ({\bf x_i}, {\bf x_j}))$`を用いて以下のようになる。<br>
`\begin{align} {\bf \alpha} = \left(K + \lambda I \right)^{-1} {\bf y} \end{align}`
ここでベクトルを１要素巡回させる行列`$P$`を用いて、ベクトル`${\bf k}$`を定義する。<br>
`\begin{align} k_i = \kappa \left( {\bf x}, P^{i} {\bf x} \right) \end{align}`
ここでKCFは上述の式の右辺の逆行列計算を避けるため、カーネル行列`$K$`が巡回行列であることを利用して、以下のように変形する。<br>
`\begin{align} {\bf \alpha} = \mathcal{F}^{-1} \left( \frac{ \mathcal{F} ({\bf y}) }{ \mathcal{F} ({\bf k}) + \lambda } \right) \end{align}`
以上を利用すると、入力画像`${\bf z}$`に対する相関出力`$\hat{{\bf y}}$`を、ベクトル`$\hat{{\bf k}} \; \left( \hat{k}_i = \kappa ({\bf z}, P^{i} {\bf x}) \right)$`を用いて、以下の式で得ることができる。<br>
`\begin{align} \hat{{\bf y}} = \mathcal{F}^{-1} \left( \mathcal{F} (\overline{{\bf k}}) \odot \mathcal{F} ({\bf \alpha}) \right) \end{align}`

@divend

@div[right]

ベクトル`${\bf k}, \hat{{\bf k}}$`の計算についても巡回行列の性質を用いて、高速化することが可能である。カーネルがドット積である場合（`$\kappa ({\bf x}, {\bf x}') = g ( \langle {\bf x}, {\bf x}' \rangle)$`）、カーネル`${\bf k}^{dp}$`は以下のように変形できる。<br>
`\begin{align} k_i^{dp} = \kappa \left( {\bf x}, P^{i} {\bf x}' \right) = g \left( {\bf x}^{T} P^{i} {\bf x}' \right) \end{align}`
さらにベクトルから巡回行列を生成する演算子`$C$`を利用して、以下のように変形できる。<br>
`\begin{align} {\bf k}^{dp} &= g \left( C({\bf x}' {\bf x}) \right) \\ &= g \left( \mathcal{F}^{-1} (\mathcal{F} ({\bf x}) \odot \mathcal{F}^{\ast} ({\bf x}') ) \right) \end{align}`
カーネルが放射基底関数である場合（`$\kappa ({\bf x}, {\bf x}') = h \left( \|{\bf x} - {\bf x}'  \|^2 \right)$`）、カーネル`${\bf k}^{rbf}$`以下のように変形できる。<br>
`\begin{align} k_i^{rbf} &= \kappa ({\bf x}, P^{i} {\bf x}') = h \left( \| {\bf x} - P^i {\bf x}' \|^2 \right) \\ &= h \left( \| {\bf x} \|^2 + \| {\bf x}' \|^2 - 2 {\bf x}^{T} P^{i} {\bf x}' \right) \\ {\bf k}^{rbf} &= h \left( \| {\bf x} \|^2 + \| {\bf x}' \|^2 - 2 \mathcal{F}^{-1} \left( \mathcal{F} ({\bf x}) \odot \mathcal{F}^{\ast} ({\bf x}') \right) \right) \end{align}`
カーネルがガウシアンカーネルである場合は、以下のように変形できる。<br>
`\begin{align} {\bf k}^{gauss} = \exp \left( - \frac{1}{\sigma^2} \left( \| {\bf x} \|^2 + \| {\bf x}' \|^2 - 2 \mathcal{F}^{-1} \left( \mathcal{F} ({\bf x}) \odot \mathcal{F}^{\ast} ({\bf x}') \right)  \right) \right) \end{align}`
<br>
__リンク__<br>
・[論文](https://arxiv.org/pdf/1404.7584.pdf)<br>
・[Matlab code](http://www.robots.ox.ac.uk/~joao/circulant/tracker_release2.zip)<br>

@divend
