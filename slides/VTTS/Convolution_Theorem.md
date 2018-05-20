#### Convolution Theorem

@div[left]

__1D Convolution Theorem__
`\begin{align} F(\nu) &= \mathcal{F} \left\{f \right\} = \int_{\mathbb{R}^n} f(x) e^{-2 \pi i x \cdot \nu} dx \\ G(\nu) &= \mathcal{F} \left\{ g \right\} = \int_{\mathbb{R}^n} g(x) e^{-2 \pi i x \cdot \nu} dx \end{align}`
`\begin{align} h(z) &= \int_{\mathbb{R}^n} f(x)g(z-x) dx \\ H(\nu) &= \mathcal{F} \left\{ h \right\} = \int_{\mathbb{R}^n} h(z) e^{-2 \pi i z \cdot \nu} dz \\ &= \int_{\mathbb{R}^n} \int_{mathcal{R}^n} f(x)g(z-x) dx e^{-2 \pi i z \cdot \nu} dz \\ &= \int_{mathbb{R}^n} f(x) \left( \int_{\mathbb{R}^n} g(z-x) e^{-2 \pi i z \cdot \nu} dz \right) dx \end{align}`


@divend

@div[right]



@divend