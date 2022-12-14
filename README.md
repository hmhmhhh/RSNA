kaggle 日記


#  20221211
[RSNA Screening Mammography Breast Cancer Detection](https://www.kaggle.com/competitions/rsna-breast-cancer-detection)に参加開始  
[このCODE](https://www.kaggle.com/code/radek1/eda-training-a-fast-ai-model-submission)を参考に解析を開始(RSNA001.ipynb).  

内容説明　　
このコンペは左右の乳房の乳がんの有無を判定するものである。
各idに対して、左右の乳がんの確率？を求めて提出する。患者数は11913人。

データの形式DICOMフォーマットが使用されている。以下のようにreadすることが可能・
~~~
example = '../input/rsna-breast-cancer-detection/train_images/10006/1459541791.dcm'
pydicom.dcmread(example)
~~~

トレインデータに11913人分の54706 このイメージデータが存在する。


解析方法  
fastai を使用([参考URL](https://qiita.com/mocobt/items/b850801c8a86d7a042b4))  
画像系のコンペでよく使用されるらしい。要確認

とりあえずそのまま提出。結果スコアF1=0.04程度。　　


#  20221212  
本日はそのほか勉強に充てる。　 


#  20221213  
[マンモグラフィーに関するdiscussion](https://www.kaggle.com/competitions/rsna-breast-cancer-detection/discussion/369262) を読む。
Breast Imaging Reporting and Data System(以下BI-RADS)はマンモグラフィーの検査結果を7段階で分類したものである。
- 0 - 追加の画像評価が必要
- 1 - 陰性
- 2 - 良性
- 3 - 良性である可能性が高い
- 4 - 疑わしい
- 5 - 悪性腫瘍の可能性が高い
- 6 - 生検で悪性が確認されたもの

データセットには0,1,2のみ存在する。0は悪性より、1,2は良性寄りである。(1,2の差は各医師による部分があるらしい)


・[このdiscussion](https://www.kaggle.com/competitions/rsna-breast-cancer-detection/discussion/369282)をみると、データの容量を小さくした画像が手に入るようだ。


[RSNA002.ipynb](https://www.kaggle.com/code/radek1/fast-ai-starter-pack-train-inference/notebook) を確認.fastaiをインストール。そのまま投稿で0.42で銅メダル。
本コンペはデータセットのダウンロードが非常に時間がかかる。。

#　20221214  
RSNA002の内容をローカルで追う予定だったが、画像のダウンロードがなかなか終わらず。。
[このdiscussion](https://www.kaggle.com/code/tomooinubushi/some-lb-probing-results-to-share/comments)を読んでみる。内容の確認コードはRSNA003。
## RSNA003について　
・テストデータセットに新しいサイトIDが存在しない。　　
・トレーニングセットとテストセットの患者IDが重複していない　　
・トレーニングセットとテストセットで画像IDが重複していない　　
・テストデータセットに新しいlateralityの値はない。　　
・テストデータセットに新しいマシンIDがある。　　
・テストデータセットに新しい view 値がない。　　
・画像数/患者数が全て4以上である　　
・サイトIDは各患者で常に同じである。　　
・年齢が常に同じである。　　
・テストデータセット内の2つのサイト間でマシンIDの重複がない。　　
・複数の撮影機で撮影された患者もいる。　　
・サイトID1の画像数＞サイトID2の画像数　　
・全患者に左右のCC画像とMLO画像がある　　
・マシンID49の画像が40%以上(トレーニングデータセットでは43%) 　　
・患者の平均年齢は56-61歳（トレーニングセットでは58.6歳）で、サイト1の患者はサイト2の患者より若い。　　
・インプラントを使用している患者は1～2%(train setでは1.4%)である。　　
陽性率は0.0204-0.0256(trainデータセットでは0.0206)である。　　







