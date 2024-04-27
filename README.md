# text-detection-ctpn

### 下載repository後請務必跟著下面步驟操作

1. __解壓縮 checkpoints.zip、ctpn.zip、lib.zip__  
   checkpoints 資料夾裡放著預訓練模型  
   ctpn 資料夾放著訓練推論模型的執行檔  
   lib 資料夾主要預處理訓練資料為主要功能  
   
3. __解壓縮 data.zip__  
   解壓縮後裡面會看到許多資料夾與 ctpn.pb, 接著下一步  

4. __Google Drive 下載檔案 (pretrain/VGG_imagenet.npy)__   
   [https://drive.google.com/file/d/1t-_PXd_I8hTjWIHTDBGHMX0wurhVr4Q0/view?usp=drive_link](https://drive.google.com/file/d/1t-_PXd_I8hTjWIHTDBGHMX0wurhVr4Q0/view?usp=drive_link)  
   並將pretrain整個資料夾放到 data/ 路徑底下  

5. __建立softlink__  
   cd 到 data/ 路徑底下, 並輸入下方指令建立softlink  
   ~/text-detection-ctpn/data$ ln -s TEXTVOC VOCdevkit2007  
   會生成一個VOCdevkit2007檔案，連結到 TEXTVOC/VOC2007/ 資料夾底下
