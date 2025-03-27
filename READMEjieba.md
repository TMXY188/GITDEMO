# 结巴分词实践
## 结巴分词的三种形式
### 全模式

import jieba
seg_list = jieba.cut("我来到北京清华大学", cut_all=True)
print("Full Mode: " + "/ ".join(seg_list))  

### 精确模式

seg_list = jieba.cut("我来到北京清华大学", cut_all=False)
print("Default Mode: " + "/ ".join(seg_list))  

### 搜索引擎模式

seg_list = jieba.cut_for_search("小明硕士毕业于中国科学院计算所，后在日本京都大学深造")  
print(", ".join(seg_list))

## 载入字典

import jieba

jieba.load_userdict("userdict.txt")

seg_list = jieba.cut("贾名扬即将是自然语言处理方面的高手", cut_all=False, HMM=False)
print("Default Mode: " + "/ ".join(seg_list))


import jieba.analyse

text = "燕山大学是河北省人民政府、教育部、工业和信息化部、国家国防科技工业局四方共建的全国重点大学，河北省重点支持的国家一流大学和世界一流学科建设高校，北京高科大学联盟成员。"

keywords = jieba.analyse.textrank(text, topK=5, withWeight=True, allowPOS=('n', 'ns', 'vn', 'nz'))

print("Top-5关键词（TextRank算法）：")
for keyword, weight in keywords:
    print(f"{keyword}: {weight:.4f}")