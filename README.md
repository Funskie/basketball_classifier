# basketball_classifier
## 使用keras(tensorflow backend)實踐transfer learning影像分類

為練習運用transfer learning 影像分類實現辨識籃球動作的專案，data source主要來自台灣各大周末聯賽公開的facebook粉絲團相簿。  

主要將動作分為三類：**運球(dribble)、上籃(layup)、投籃(shoot)**  
training data各自為dribble：967、layup：869、shoot：945張images，testing datas各自100張。  
下為專案架構：
```
├── checkpoints/
├── coreml_models/
├── dataset/
│   ├── test/
|   |   ├─ dribble/
|   |   ├─ layup/
|   |   └─ shoot/
│   └── train/
|       ├─ dribble/
|       ├─ layup/
|       └─ shoot/
├── models/
├── scripts/
│   ├── covert_model_to_coreml.ipynb
|   ├── data_collect.ipynb
│   └── model_training.ipynb
├── requirements.txt
├── README.md
```
- **checkpoints**：存放訓練時loss較前幾次小的model的資料夾。  
- **models**：存放從**checkpoints**資料夾中測試完準確率較高的模型。  
- **coreml_models**：存放從**models**資料夾中的*.h5 model所轉成的*.mlmodel檔案，拿來丟進xcode建立ios行動裝置app等。  
- **dataset**：存放taining data及testing data，以資料夾名稱作為分類label。  
- **scripts**：存放專案相關的code，**data_collect.ipynb**主要利用FB的Graph API及爬蟲抓取公開粉絲團的籃球比賽照片至local，**model_training.ipynb**作主要
訓練與測試到儲存模型的工作，**covert_model_to_coreml.ipynb**利用coremltools.converters.keras.convert將keras的h5模型檔轉成apple的coreml_model格式。  
- **requirements.txt**：*待續*
