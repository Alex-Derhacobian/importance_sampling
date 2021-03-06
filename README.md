# A Fun and Fast Investigation of Importance Sampling

## What is importance sampling? ##

Importance sampling is a technique for estimating properties of one distribution by sampling from a different distribution. This can be used when when we want to estimate the property of some distribution <img src="https://render.githubusercontent.com/render/math?math=f">, but we don't know how to sample from <img src="https://render.githubusercontent.com/render/math?math=f">. Importance sampling is a generalization of Monte Carlo integration, where we estimate <img src="https://render.githubusercontent.com/render/math?math=P(X > \alpha)"> by calculating 

<img src="https://render.githubusercontent.com/render/math?math=P(X > \alpha) = \frac{1}{N}\sum_{i=1}^n h(X_i)">

where <img src="https://render.githubusercontent.com/render/math?math=X_1, \dotsc, X_N \sim f"> and 

<img src="https://render.githubusercontent.com/render/math?math=h(X_i) = \begin{cases} 1 \hspace{0.5cm } X_i > \alpha \\ 0 \hspace{0.5cm } X_i \leq \alpha \end{cases}">


But what if the region where <img src="https://render.githubusercontent.com/render/math?math=X > \alpha"> is very small, maybe even too small for any random sample from <img src="https://render.githubusercontent.com/render/math?math=f"> to capture the area of this region? That is when importance sampling is used. Importance sampling encourages sampling from the region of interest, and accounts for this sampling bias by reweighting <img src="https://render.githubusercontent.com/render/math?math=f">. To understand this, we will first consider Monte Carlo integration in a continuous space: 

<img src="https://render.githubusercontent.com/render/math?math=P(X > \alpha) = \int_\mathcal{P} h(x)f(x)dx">

Let <img src="https://render.githubusercontent.com/render/math?math=g"> be a probability density that we know how to sample from. Then, we can write

<img src="https://render.githubusercontent.com/render/math?math=P(X > \alpha) = \int_\mathcal{P} h(x)f(x) dx = \int_\mathcal{P}  \frac{h(x)f(x)}{g(x)} g(x) dx = E_g[Y]">

where <img src="https://render.githubusercontent.com/render/math?math=Y = \frac{h(x)f(x)}{g(x)}"> You will show that importance sampling can reduce the variance of probability estimates in regions of low density. 
