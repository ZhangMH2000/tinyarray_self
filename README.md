# tinyarray

### 前言

hi，我是小洁。这是我基于自己的数据分析需求写的R包，很高兴被你看到了。我会在公众号《生信星球》更新这里面一些好用的小函数，也做一些其他的分享。

###  安装方式

#### 1.在线安装

```
if(!require(devtools))install.packages("devtools")
if(!require(tinyarray))devtools::install_github("xjsun1221/tinyarray",upgrade = F)
```

#### 2.本地安装

点击本页面的绿色按键`code`然后点击`Download ZIP`，下载到你的工作目录下，用`devtools::install_local("tinyarray-master.zip",upgrade = F,dependencies = T)`安装。

#### 3.安装R包过程中可能出现的问题及解决办法

如果报错说xx包找不到，那就安装它。
如果报错信息中出现http,404,internet,url等关键词，说明是网络问题，一般来说本地安装即可解决。

### 函数介绍

#### 1.几个常用绘图函数

都是字面意思：表达矩阵可视化其乐无穷。

draw_heatmap(),draw_volcano(),draw_venn(),draw_boxplot()

#### 2.GEO芯片下游分析

geo_download() : 提供geo编号，返回表达矩阵、临床信息表格和使用的平台编号。

find_anno():查找芯片平台注释

get_deg() ：提供芯片表达矩阵、分组信息、探针注释，返回差异分析结果。

multi_deg() : 多个分组（最多5个）的差异分析

如果是想一步到位，做出差异分析常见的几张图，可以用get_deg_all() 和multi_deg_all() 

这一部分主要是融合跟简化一下GEOquery、Annoprobe、limma的差异分析。

quick_enrich() : 简单直观的富集分析

##### 详细的介绍在：

[我写了一个R包，简化芯片的差异分析](https://mp.weixin.qq.com/s/YQQoDsE5JaKpgFGlbEfQNg)

[我完善了那个R包，可以简化多组的差异分析啦](https://mp.weixin.qq.com/s/j5IB_MQ0zeOCe1j_ahwtdQ)

#### 3.表达矩阵探索

make_tcga_group():根据TCGA的样本命名规则，快速得出分组

trans_array():替换矩阵的行名，比如把表达矩阵的探针名替换为基因名

sam_filter():去除tcga中的重复tumor样本

match_exp_cl():匹配tcga表达矩阵与临床信息

trans_exp():将tcga或tcga+gtex数据进行基因id转换

t_choose():批量做单个基因的t检验

cor.full()和cor.one() :批量计算基因间的相关性

dumd():统计数据框每一列各有多少个取值

#### 4.生存分析及可视化

point_cut():批量计算生存分析最佳截点

surv_KM():批量做KM生存分析，支持用最佳截点分组

surv_cox():批量做单因素cox，支持用最佳截点分组

[太好用了！批量生存分析加画图，一步到位，还支持最佳截点~](https://mp.weixin.qq.com/s/WYBhGxfGg6QFUPHFBashaA)

exp_boxplot()：给感兴趣的基因画T-N箱线图

exp_surv()：给感兴趣的基因画KM-plot

box_surv(): 给感兴趣的基因画箱线图和KM-plot

#### 5.网络图相关

hypertest():批量做mRNA和lncRNA的超几何分布检验

plcortest():批量做mRNA和lncRNA的相关性检验

interaction_to_edges():根据关系表格生成网络图的连接表格

edges_to_nodes():根据连接表格生成节点表格

还有一个函数叫ggheat,也是字面意思，用ggplot2的函数来画热图，这个主要是为了拼图对齐和图例收集。

##### 详细的介绍在：
[披着ggplot皮的pheatmap,深夜激动更新我的包](https://mp.weixin.qq.com/s/WhsBf6QAhVXeXeScM59cSA)

### 还会继续更新

写于2021.1.26

更新日志：

#### 2.1.1
limma更新，第一列为ID，随之改了get_deg和draw_volcano

ggplot2更新，手动指定颜色必须加values=，已加

ifelse更新，允许矩阵数据，生成结果也为矩阵，为此改了表达矩阵箱线图、KM图系列

表达矩阵与分组信息的匹配

#### 2.1.2
mRNA与lncRNA都有时矩阵去重

#### 2.1.5

GEO下载的表达矩阵有异常值时不再报错，而是只给个warning啦

#### 2.1.6

解决mac tab键编码方式报错问题

#### 2.1.7

draw_heatmap 添加参数scale，F即为原矩阵画图，不scale.

#### 2.1.8

draw_heatmap 添加参数main，标题

#### 2.1.9

surv_cox 输出结果小数点位数不限制（因为有些p值太小，会变成零）

### 2.2.0

检查了exp_boxplot之前的所有函数及其帮助文档，quickenrich和make_tcga_group不再报warning
