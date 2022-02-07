# Long Short-Term Memory
![struct](https://github.com/yifan-07/LSTM/blob/main/picture/LSTM_struc.png?raw=true)
* 核心：透過閘門(gate)進行調控，決定記憶的儲存與使用。
* 組成： input gate、output gate、memory cell、forget gate
## Cell State 
![cell_state](https://github.com/yifan-07/LSTM/blob/main/picture/cell_state.png?raw=true)
單元狀態(cell state)：資訊從一個單元帶至下一個單元，透過粉色閘門做控制。(上圖由左至右之水平線)
## Forget Gate
![forget_gate](https://github.com/yifan-07/LSTM/blob/main/picture/forget_gate.png?raw=true)
決定是否清除memory
## Input Gate
![input_gate](https://github.com/yifan-07/LSTM/blob/main/picture/input_gate.png?raw=true)
控制是否輸入新的值
## Output Gate
![output_gate](https://github.com/yifan-07/LSTM/blob/main/picture/output_gate.png?raw=true)
控制是否將計算出的值output，若無輸出則為0</br>

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
