# 打比赛过程记录
初赛截止日期10月21日    
复赛20201022-20201106：初赛前100名中挑50名    

# 命名实体识别(NER)

## 1 

Bert  Albrtt  RoBERTa

数据增强  

模型融合  

# 优化点
特征工程
调参
模型融合

## 验证方法选择
- 留出法  
缺点：  
1.最终模型与参数的选取将极大程度依赖于你对训练集和测试集的划分方法；  
2.该方法只用了部分数据进行模型的训练

- K折交叉验证法(Cross-Validation)  
y一般划分为K=5或10  
- 自助法  
自助法其实就是K=n的交叉验证  

（因为数据集比较小，可以尝试使用后两者进行优化对比）

## 模型融合
参考知乎 https://zhuanlan.zhihu.com/p/25836678  

- Voting  

- Averaging  
进阶的如加权平均

- Bagging  
Bagging就是采用有放回的方式进行抽样，用抽样的样本建立子模型,对子模型进行训练，这个过程重复多次，最后进行融合。大概分为这样两步：
1. 重复K次
有放回地重复抽样建模  
训练子模型  

2. 模型融合

- Boosting  
基于Boosting思想的有AdaBoost、GBDT等  
随机森林、Adaboost、GBDT、XGBoost的区别是什么？  
- Stacking  


BERT+BiLSTM+CRF  
BERT+IDCNN+CRF  
BERT多层表示的动态权重融合  

## 解码器
- Softmax  
- CRF  
- MEMM
- HMM
softmax没有直接考虑输出的上下文关联，CRF在输出端显式的考虑了上下文关联。  

CRF转移矩阵，重点理解。  

https://kexue.fm/archives/5542  
https://kexue.fm/archives/7213  

