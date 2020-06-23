# SIIM-ISIC-Melanoma-Classification
Identify melanoma in lesion images  
Framework : Tensorflow / Keras  
### Point
- Very HIGH class imbalance  
 


## Base architecture
1. efficientnet b0   
  or **efficientnet b2** is best in my source  
2. adam optimizer  


## Solutions  
- focal loss  
- over and under sampling - (undersampling)  
- augmentation  
  * ~~rotation_range~~
  * width_shift_range=0.2
  * height_shift_range=0.2
  * vertical_flip=True
  * horizontal_flip=True
  * zoom_range=[1.0, 1.3]
  * ~~random_erase~~
  * rotate 90 = True
- ensemble (to do)
  * variety input size (256, 512, 1024 ...)
  * with rank data (?)
- weight balancing (to do)      
  * Must not use 'focal loss' and 'weight balancing' together
- noisy-student
  * stochastic depth
  * dropout
  * rand augment
- 