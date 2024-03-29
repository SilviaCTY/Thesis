# 碩士論文
## 線上評論助益性預測：文本特徵性能差異分析
* 先前文獻很少去比較不同單一特徵對評論助益性的影響，為了探討多維度文本特徵對線上評論助益性的影響，本研究將先前有關於評論助益性的文獻進行全面性搜索、統整特徵，並且比較不同特徵的效果如何。
## 研究方法
* 資料集:Julian McAuley所創建的Amazon product data（1996年～2014年）（應用程式、美容、CD與黑膠唱片、服飾、手機與配件、雜貨和美食、電影與電視、電玩遊戲）
### 資料前處理
* 第一步先刪除總投票數少於10票的評論，再將有幫助投票數除以投票總數，得到評論助益性比率，
* 第二步以0.5為臨界值，把評論助益性分數做轉換，評論助益性比率大於0.5劃分為有幫助的評論，小於0.5則劃分為無幫助的評論
* 第三步對劃分好的評論資料做隨機抽樣，抽樣的比率為2正樣本（有幫助）：1負樣本（無幫助）
### 特徵萃取
* 文本特徵（Unigram、Bigram）
* 詞法特徵（評論長度、句子數、句子平均字數、大小寫、是否正確使用大寫、Type-Token Ratio、拼寫錯誤）
* 句法特徵（可讀性指標、POS標記、標點符號）
* 詞彙特徵（LIWC 辭典、NRC Emotion辭典、SentiWordNet）
* 話語特徵（詞嵌入、主題模型）
* 評價特徵（評論的評分、評論的極端、評論的天數）
### 特徵組合
* 特徵組合1：文本特徵+詞法特徵
* 特徵組合2：文本特徵+詞法特徵+句法特徵
* 特徵組合3：文本特徵+詞法特徵+句法特徵+詞彙特徵
* 特徵組合4：文本特徵+詞法特徵+句法特徵+詞彙特徵+話語特徵
* 特徵組合5：文本特徵+詞法特徵+句法特徵+詞彙特徵+話語特徵+評價特徵
* 特徵組合6：文本特徵+評價特徵
### 個別特徵
* 詞彙特徵、話語特徵則是使用NLP的方式，在評論文本中找出情感，將非結構化的詞語轉換成向量，用來探討詞語背後隱藏的含義，所以把詞彙特徵和話語特徵的7種自然語言處理工具做為個別特徵，比較不同情感工具、不同維度的向量工具，他們的效能差異。
### 模型建構
* 分類模型（邏輯回歸、天真貝氏、決策樹、隨機森林、XGBoost）
* 回歸模型（線性回歸、決策樹、支援向量回歸、KNN、隨機森林、XGBoost）
### 預測與評估
* 十折交叉驗證
* 分類模型評估指標:準確率（Accuracy）、精確率（Precision）、召回率（Recall）、F1分數（F1-score）、AUC
* 回歸模型評估指標:平均絕對誤差（MAE）、平均平方誤差（MSE）、決定係數（R-squared）、皮爾森積差相關分析（Pearson Correlation）
### 假設檢定
* 詞法特徵（評論長度、句子數、平均句子長度、大寫、是否正確使用大寫、大寫的比率、小寫、小寫的比率、Type-Token Ratio、拼寫錯誤）、句法特徵 （Flesch Reading Ease、Flesch-Kincaid Grade Level、Gunning Fog Index、Automated Readability Index、The Coleman-Liau Index、The SMOG Index、標點符號）、詞彙特徵（SentiWordNet）、評價特徵（評論的評分、評論的極端、評論的天數）以上簡單變數做T檢定
