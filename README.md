# text-detection-ctpn

## 下載repository後請務必跟著下面步驟操作

1. __解壓縮 checkpoints.zip、ctpn.zip、lib.zip、data.zip__   
   解壓縮完的檔案架構如下 (圖中有Zone.Identifier不需理會)
   
   ### text-detection-ctpn(根目錄)  
   ![image](https://github.com/g0983230881/text-detection-ctpn/assets/54482415/94c57cbc-90c4-44b9-af29-4e88e3f7b075)  

      ### checkpoint folder  
      ![image](https://github.com/g0983230881/text-detection-ctpn/assets/54482415/6d645503-b27e-4bd7-9d15-5d021a585ec6)  

      ### ctpn folder  
      ![image](https://github.com/g0983230881/text-detection-ctpn/assets/54482415/70904b7e-0d98-4aa4-82b6-7187a2456349)  

       
      ### lib folder  
      ![image](https://github.com/g0983230881/text-detection-ctpn/assets/54482415/77e5f632-918c-4133-a8ed-c8d79be43a40)  

      ### data folder  
      ![image](https://github.com/g0983230881/text-detection-ctpn/assets/54482415/0c5fc4d4-fcf8-4234-be43-198771af883f)  

2. __Google Drive 下載檔案 (pretrain/VGG_imagenet.npy)__   
   [https://drive.google.com/file/d/1t-_PXd_I8hTjWIHTDBGHMX0wurhVr4Q0/view?usp=drive_link](https://drive.google.com/file/d/1t-_PXd_I8hTjWIHTDBGHMX0wurhVr4Q0/view?usp=drive_link)  
   並將pretrain整個資料夾放到 data/ 路徑底下  

3. __建立softlink__  
   cd 到 data/ 路徑底下, 並輸入下方指令建立softlink  
   ~/text-detection-ctpn/data$ ln -s TEXTVOC VOCdevkit2007  
   會生成一個VOCdevkit2007檔案，連結到 TEXTVOC/VOC2007/ 資料夾底下  

4. __環境配置__  
   已測試環境:  
   python               3.6.13  
   opencv-python        3.4.0.12  
   tensorflow-gpu       1.15.0  
   從源專案的環境配置到可以Demo實作推論、訓練模型的詳細步驟,  
   請看專案內的word: text-detection-ctpn-gpu 環境建置.docx  
   origin repository: [https://github.com/eragonruan/text-detection-ctpn](https://github.com/eragonruan/text-detection-ctpn)  

5. __推論與訓練細節__  
   ## Demo
   若想用 VGGnet_fast_rcnn_iter_50000.ckpt 實作 ./ctpn/demo.py,  
   則取消註解 lib/rpn_msr/proposal_layer_tf.py line45: cfg_key=cfg_key.decode('ascii')  
   
   若想用 ctpn.pb 實作 ./ctpn/demo_pb.py  
   則註解 lib/rpn_msr/proposal_layer_tf.py line45: cfg_key=cfg_key.decode('ascii')

   實作的照片請放在 ~/text-detection-ctpn/data/demo/ 資料夾底下  

   ## Training
   將自己的訓練資料放在 lib/prepare_training_data/ 底下, 要先修改程式裡的路徑  
   split_label.py 輸入路徑如下  
   path: 照片資料夾目錄  
   gt_path: 標記資料夾目錄  
   
   5.1 執行指令: ~/prepare_training_data$ python split_label.py  
   輸出 re_image、label_tmp 資料夾  
   re_image 是重新縮放照片大小, label_tmp 是找出座標中最大與最小的x,y座標且輸出他們  
   
   5.2 執行指令: ~/prepare_training_data$ python ToVoc.py  
   輸出 TEXTVOC 資料夾, 再把該資料夾移到 data/ 底下  
