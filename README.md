kaggle 日記


#20221211
[RSNA Screening Mammography Breast Cancer Detection](https://www.kaggle.com/competitions/rsna-breast-cancer-detection)に参加開始  
[このCODE](https://www.kaggle.com/code/radek1/eda-training-a-fast-ai-model-submission)を参考に解析を開始(RSNA001.ipynb).  

内容説明　　
このコンペは左右の乳房の乳がんの有無を判定するものである。
各idに対して、左右の乳がんの確率？を求めて提出する。患者数は11913人。

データの形式DICOMフォーマットが使用されている。以下のようにreadすることが可能・
'''
example = '../input/rsna-breast-cancer-detection/train_images/10006/1459541791.dcm'
pydicom.dcmread(example)
'''

トレインデータに11913人分の54706 このイメージデータが存在する。


解析方法  
fastai を使用([参考URL](https://qiita.com/mocobt/items/b850801c8a86d7a042b4))  
画像系のコンペでよく使用されるらしい。要確認

とりあえずそのまま提出。結果スコアF1=0.04程度。　　


#20221212  
本日はそのほか勉強に充てる。　 










