# YOLOv4_tensorflow2
> A implementation of YOLOv4 with tensorflow2

## Environment
- python 3.8
- tensorflow 2.4

## Model weights
- yolo4_weight.h5 : Trained on COCO2017, 416 * 416
- yolo4_voc_weight.h5 : Trained on VOC07+12+COCO, 416 * 416

## Training VOC
1. 準備資料
    - 使用VOC格式訓練，下載VOC2007和VOC2012的資料放在VOC/VOC2007目錄中
    - 會使用到annotations, ImageSets, JPEGImages等三個資料夾
    - 將下載的資料依照資料夾分別放置
    - 若是使用自己的資料，使用VOC格式標註資料並依上述流程操作
2. 處理資料
    - VOC資料已經切好train/val/test, 依據想使用的部分在Imagesets/Main中分別建立新的train.txt, val.txt, test.txt(名稱可修改)
    - 在voc_annotation.py中設定annotation_mode=2(已經切好train/val/test)
    - 在voc_annotation.py中設定VOCdevkit_sets = [('2007', 'train'), ('2007', 'val')], 其中'2007'要符合VOC/VOC2007的名稱, 'train'和'val'則是符合Imagesets/Main中使用的train.txt/val.txt名稱(若有修改名稱則兩邊都要改)
    - 在此Github則是修改名稱為[('2007', 'train0712'), ('2007', 'val0712')], 最後生成要訓練的檔案名稱就是2007_train0712.txt, 2007_val0712.txt.
3. 訓練
    - 使用train.py訓練
    - eager模式若用不到可註解掉
    - 修改以下五個路徑至自己指定的資料夾和檔案 : classes_path, anchors_path, model_path, train_annotation_path, val_annotation_path
4. 預測
    - 會使用到yolo.py和predict.py
    - 先至yolo.py中修改model_path和classes_path
    - model_path指向訓練好的權重, 放在logs資料夾中
    - classes_path指向所要偵測的classes.txt
    - 最後執行predict.py及可預測
5. 整合Jupyer notebook
    - 為方便使用已經將整個流程整理成notebook形式
    - 可邊執行邊檢視結果

# Reference
https://github.com/bubbliiiing/yolov4-tf2
