# 背景介绍

## 推荐系统的产生
在网络技术不断发展和电子商务规模不断扩大的背景下，商品数量和种类快速增长，用户需要花费大量时间才能找到自己想买的商品，这就是信息超载问题。为了解决这个难题，个性化推荐系统（Recommender System）应运而生。

个性化推荐系统是信息过滤系统（Information Filtering System）的子集，它可以用在很多领域，如电影、音乐、电商和 Feed 流推荐等。个性化推荐系统通过分析、挖掘用户行为，发现用户的个性化需求与兴趣特点，将用户可能感兴趣的信息或商品推荐给用户。与搜索引擎不同，个性化推荐系统不需要用户准确地描述出自己的需求，而是根据用户的历史行为进行建模，主动提供满足用户兴趣和需求的信息。

1994年明尼苏达大学推出的GroupLens系统一般被认为是个性化推荐系统成为一个相对独立的研究方向的标志。该系统首次提出了基于协同过滤来完成推荐任务的思想，此后，基于该模型的协同过滤推荐引领了个性化推荐系统十几年的发展方向。

## 应用场景

### 电商领域

在电商领域，比较典型的是亚马逊的个性化推荐系统，被称为“推荐系统之王”。亚马逊有 20%~30% 的销售额来自于推荐系统。主要形式包括个性化推荐列表、相关推荐列表及打包销售等。

+  个性化推荐列表：将那些和用户喜欢的物品比较相似的物品，或者用户好友喜欢的物品推荐给用户。
+  相关推荐列表：当用户购买一件物品后，将那些购买此物品的用户也经常购买的其他物品，或者浏览过此物品的用户也经常购买的其他物品推荐给用户。
+  打包销售：当用户单击某个物品的购买按钮时，将那些其他用户在购买此物品时，连同购买的其他物品推荐给用户。


### 电影视频
+ Netflix:基于物品的推荐
+ YouTube,Hulu

#### 音乐
+ Pandora:专家标记
+ Last.fm:用户行为

### 社交网络
+ Facebook
+ Twitter

### 阅读
+ Goodle Reader

### 基于位置的服务
+ Foursquare

### 个性化邮件
+ Tapestry

### 广告
+ Facebook


## 推荐系统的方法

传统的个性化推荐系统方法主要有：

+ 协同过滤推荐（Collaborative Filtering Recommendation）：该方法是应用最广泛的技术之一，需要收集和分析用户的历史行为、活动和偏好。它通常可以分为两个子类：基于用户 （User-Based）的推荐和基于物品（Item-Based）的推荐。该方法的一个关键优势是它不依赖于机器去分析物品的内容特征，因此它无需理解物品本身也能够准确地推荐诸如电影之类的复杂物品；缺点是对于没有任何行为的新用户存在冷启动的问题，同时也存在用户与商品之间的交互数据不够多造成的稀疏问题。值得一提的是，社交网络或地理位置等上下文信息都可以结合到协同过滤中去。

+ 基于内容过滤推荐（Content-based Filtering Recommendation）：该方法利用商品的内容描述，抽象出有意义的特征，通过计算用户的兴趣和商品描述之间的相似度，来给用户做推荐。优点是简单直接，不需要依据其他用户对商品的评价，而是通过商品属性进行商品相似度度量，从而推荐给用户所感兴趣商品的相似商品；缺点是对于没有任何行为的新用户同样存在冷启动的问题。

+ 组合推荐（Hybrid Recommendation）：运用不同的输入和技术共同进行推荐，以弥补各自推荐技术的缺点。
近些年来，深度学习在很多领域都取得了巨大的成功。学术界和工业界都在尝试将深度学习应用于个性化推荐系统领域中。深度学习具有优秀的自动提取特征的能力，能够学习多层次的抽象特征表示，并对异质或跨域的内容信息进行学习，可以一定程度上处理个性化推荐系统冷启动问题

## 推荐系统的组成

（一）、画像

1、定义：画像指的是从用户产生的各种数据中挖掘和抽取用户在不同属性上的标签，如年龄、性别、职业、收入、兴趣等。

2、画像生成路径

+ 用户行为日志收集和存储（离线数据和实时数据）
+ 用户行为提取，特征加工，生成特征向量（静态特征和动态特征）
+ 利用有用户属性标签的数据作为有标注数据来训练画像预测模型
+ 对更多的有标签用户属性来进行预测

3、画像分类

按照数据类型划分：（目前使用较多的分类）

+ 静态画像：用户相对稳定的信息。缺点：实时性不够，过于粗糙
+ 动态画像：用户不断变化的行为信息，根据用户行为将物品的结构化结果传递给用户

按照画像性质进行划分

+ 定性画像（定性描述用户或内容的特征信息）
+ 定量画像（统计类标签，预测类标签）
+ 定性画像+定量验证

在以上的三种画像分类中定性画像，是通过用户的行为习惯，挖掘出的标签信息，一般可以深入继续挖掘用户的动机，但这类的画像标签，一般无法用数据直接验证，只能定性理解。与定性画像不同，定量画像有充分数据验证，可以通过数据统计和分析来进行验证，但他对统计的要求比较高，且一般难以挖掘用户情感倾向和行为操作背后的原因和深层次的动机。最优的方法就是第三种将二者结合起来的方法，这种方法既能通过数据描述也能从用户行为中验证画像的准确性，但将二者结合的方法会存在工作量大的问题，且定性画像与定量画像之间可能存在相悖的结论，需要较为丰富的经验进行论证。

4、画像验证

+ 准确率
+ 覆盖率

准确率指的是被打上正确标签的用户比例，准确率是用户画像最核心的指标，一个准确率非常低的标签是没有应用价值的。通常会通过以下两种方法来评估标签的准确率

+ 在标注数据集里留一部分测试数据用于计算模型的准确率
+ 在全量用户中抽一批用户，进行人工标注，评估准确率（数据更可信）
覆盖率指的是被打上标签的用户占全量用户的比例，同理一个覆盖率太低的标签，是没有应用价值的。通常对于覆盖率的评估是以某一个标签覆盖的用户比例和覆盖用户的人均标签数作为评估标准

（二）、召回

1、定义： 从全量的文章库中按照一定的规则筛选出一个文章候选池，一般的规则有：按照机型，地域，热点和用户-文章协同过滤
2、召回的作用：从全量内容中，第一次粗过滤，筛选出大概率适合展示给用户的内容，减少后续计算的复杂度

3、常用召回方法：

基于热点召回：基于热点事件的召回，通过对热点事件相关的内容进行计算，同时匹配可能感兴趣的用户，进而进行推荐展示

基于地域召回：计算用户和内容的位置信息，以地理位置作为匹配关联的核心因素，进而圈选出相匹配的用户和内容

协同召回（基于用户和内容两种召回方法）：主要分为基于用户的协同召回和基于内容的协同召回两种方法，以基于用户的协同召回为例进行说明：

当需要对用户A进行推荐时，找到和A有相似兴趣的其他用户群B，把B喜欢看的，而A还没有看过的内容进行召回，进而推荐给A用户

（三）、排序

1、定义： 是推荐系统中召回后的一个模块，主要是一个或多个指标为依据，进行打分，一般将得分按照倒序进行排列

2、排序的作用

高效：帮助用户找到想要的商品（新闻/音乐/……），发掘长尾
降噪：将重复的文章进行合并，剔除垃圾信息
提高用户访问的频次：让用户频繁访问，并总是能找到他们想要阅读和购买的物品

3、衡量指标

CTR (Click Through Rate)：当给用户推荐他真实喜欢的内容时，用户就会产生比较大的点击意愿，进而产生较高的点击。 
