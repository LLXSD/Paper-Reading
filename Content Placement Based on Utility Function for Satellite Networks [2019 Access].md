文章出处：Wang E, Lin X, Zhang S. Content Placement Based on Utility Function for Satellite Networks[J]. IEEE Access, 2019, 7: 163150-163159.
## 内容概述
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;本文研究的是**不同卫星之间内容如何分配**的问题，基于内容的popularity优化命中率。文章同样是基于每颗卫星上都配备cache的假设，与[Globecom'2016]的区别在于解决的不是星地缓存节点内容如何分配的问题，而是不同卫星内容如何分配。根据内容的popularity，分为MPC(Most Popular Content)和GPC(General Popular Content )，提出多颗卫星各缓存一份MPC的PT策略(Parallel Transmission strategy)，和多颗卫星共同缓存一份GPC的CT策略(Cooperative Transmission strategy)。
模型最终的评价指标是**SDP(successful delivery probability）**，这一指标的得出与信道质量是有关系的。考虑到地面用户和卫星用户由于共享频谱而引起的干扰问题，文章首先对信道模型进行建模，得出所需数据，经过一系列的推导得出最后表达式。文章实验部分利用STK+Matlab进行数据仿真，探究不同参数值对于SDP值的影响。

*特别地，文章对干扰问题进行简化，认为赤道附近人口密度大、地面用户更多，因此存在干扰，而在其他位置即使存在频谱共享的情况，也认为不存在干扰。这种简化方式也不一定合理，最好还是有实际数据支撑做出一些假设。*

## 简单介绍
文章首先分析卫星用户通信的场景，由于地面用户和卫星用户频谱资源存在共享的问题，因此会存在干扰，不同的地面用户密度的干扰情况是不同的，给出了通信场景如下，其中卫星用户是primary，地面用户是secondary：
![younghz的Markdown库](https://img-blog.csdnimg.cn/20200726233054858.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpbkxMWA==,size_16,color_FFFFFF,t_70)

文章将内容分配抽象成两个最优化问题，一个解决MPC和GPC比例，一个解决GPC的不同部分在不同若干颗卫星上如何缓存。前者主要优化的指标是max cache service probability，后者主要针对开销min cost (relay transmission +storage)。

本文中提出的是针对低轨卫星的cluster-centric的解决方案，即卫星是分cluster的，不同用户密度区域的cluster的大小不同，包含的卫星数不同。

*Comment*：文章的仿真实验部分交待地不是特别清楚，没有介绍被用来与理论值作比较的仿真实验结果是如何得到的，因此对结果存疑；文章的创新点在于根据内容的popularity解决不同卫星如何分配内容的问题，这是不同于之前针对星地之间如何分配内容的文章的地方，考虑到了多星协作，而不只是单星的场景。
