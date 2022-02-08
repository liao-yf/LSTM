# Long Short-Term Memory
![struct](https://github.com/yifan-07/LSTM/blob/main/picture/LSTM_struc.png?raw=true)
* 核心：透過閘門(gate)進行調控，決定記憶的儲存與使用。
* 組成： input gate、output gate、memory cell、forget gate

## Activation Function
激活函數(activation function)：  
對上個節點的輸出進行非線性轉換。透過非線性轉換獲取充分的特徵組合，使得神經網路可以充分學習更多。常見的激活函數：sigmoid, tanh, ReLU。在LSTM裡常用的激活函數為sigmoid, tanh。  
* Sigmoid：
可用於二分類。其輸出值介於0到1之間，且為連續變數放於求導數。  
* Tanh：  
又稱雙曲正切曲線，其值取值為[-1,1]，為sigmoid的變形。優點為收斂較快速，缺點為容易發生梯度消失。  

## Cell State 
![cell_state](https://github.com/yifan-07/LSTM/blob/main/picture/cell_state.png?raw=true)
單元狀態(cell state)：  
  神經元訊息記憶空間，接收遺忘門及輸入門的訊息。如圖示，將遺忘門輸出之向量和上一個神經元狀態(Ct-1)作逐點乘積，輸入門輸出向量和候選向量作逐點乘積，並將兩者相加以獲得神經元狀態Ct。  
## Forget Gate
![forget_gate](https://github.com/yifan-07/LSTM/blob/main/picture/forget_gate.png?raw=true)
遺忘門(forget gate)：  
在神經元中選擇丟棄過去哪些訊息，輸入時間點t之資料向量及時間點t-1的輸出向量ht-1，藉由sigmoid函數激活。sigmoid函數值介於0 ~ 1之間的值，而這個值表示gate被打開的程度。當輸出值為1時，保留輸出為0時丟棄  
## Input Gate
![input_gate](https://github.com/yifan-07/LSTM/blob/main/picture/input_gate.png?raw=true)
在神經元中決定記憶哪些訊息，輸入時間點t的資料向量及時間點t-1的輸出量向ht-1，並藉由sigmoid函數激活。另外利用tanh函數將時間點t的資料向量及時間點t-1的輸出向量ht-1作用為一組候選值向量，而後將兩組結果作相乘。  
## Output Gate
![output_gate](https://github.com/yifan-07/LSTM/blob/main/picture/output_gate.png?raw=true)
輸出門(output gate)：  
神經元中決定哪些訊息要輸出給下一個時間，輸入時間點t的資料向量以及時間點t-1的輸出向量ht-1，藉由sigmoid函數進行激活。經函數激活後輸出值介於0~1之間，輸出為1時保留，輸出為0時丟棄。另外將神經元狀態Ct經由tanh激活後輸出-1到1的向量，將兩者進行逐點乘積以獲得時間點t支輸出函數ht。  

## Python
### Package
* sklearn.preprocessing：MinMaxScalew 
* keras.models：Sequential
* keras.layers：Dense, LSTM, Dropout
* tensorflow.keras.optimizers：SGD
* sklearn.metrics：mean_squared_error

### Example
* IBM股價資料  
資料說明：使用IBM 2006/01/01 ~ 2018/01/01之開盤資料，以2016年為切割點，將2016年以前之資料作為訓練資料，2017年以後的資料做為測試資料。 
![open](https://github.com/yifan-07/LSTM/blob/main/picture/stock_price.png?raw=true)
(藍色員訓練集區間之股價變化；橘色為測試集區間之股價變化)  
分析說明：  
step 1 > 將資料做最大最小值標準化(MinMaxScaler)，給定最大值為1，最小值為0，將數據縮放置[0, 1]之間  
step 2 > 60天前的開盤資料預測當天開盤價  
step 3 > 建立LSTM模型  
step 4 > 預測開盤  
![predict](https://user-images.githubusercontent.com/35762304/152771971-5eae2c45-50c3-435f-8862-502d7b3a645d.png)



<br>source </br>
* https://colah.github.io/posts/2015-08-Understanding-LSTMs/
* https://tengyuanchang.medium.com/%E6%B7%BA%E8%AB%87%E9%81%9E%E6%AD%B8%E7%A5%9E%E7%B6%93%E7%B6%B2%E8%B7%AF-rnn-%E8%88%87%E9%95%B7%E7%9F%AD%E6%9C%9F%E8%A8%98%E6%86%B6%E6%A8%A1%E5%9E%8B-lstm-300cbe5efcc3
* https://ithelp.ithome.com.tw/articles/10276865
* https://codingnote.cc/zh-tw/p/176736/
* https://clay-atlas.com/blog/2019/10/22/machine-learning-notes-tanh-function/
