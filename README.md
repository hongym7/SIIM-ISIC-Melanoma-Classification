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
  * ~~rotate 90 = True~~
- ensemble (to do)
  * variety input size (256, 512, 1024 ...)
  * with rank data (?)
- weight balancing (to do)      
  * Must not use 'focal loss' and 'weight balancing' together
- noisy-student
  * stochastic depth
  * dropout
  * rand augment


## Result
- train_ext_data_06_5_9
    - _ : [0.921] b2 zoom_range=[1.0, 1.3]    
    - 1 : [0.922] b2 zoom_range=[1.0, 1.3] brightness_range=[0.7, 1.0] epoch15
    - 2 : [0.907] b2 zoom_range=[1.0, 1.3] brightness_range=[0.7, 1.0] epoch10
- train_ext_data_06_5_12  
    - _ : [0.914] b2 25000(more than 06_5_9_)
- train_ext_data_06_5_13  
    - _ : [0.922] b3 zoom_range=[1.0, 1.3]  
    - 1 : [0.906] b3 zoom_range=[1.0, 1.3] rot90
    - 2 : [0.914] b4 zoom_range=[1.0, 1.3]
    - 3 : [0.912] b3 zoom_range=[1.0, 1.4]  
    - 4 : [0.924] b3 zoom_range=[1.0, 1.4] brightness_range=[0.7, 1.0]   
    - 5 : [0.915] b3 zoom_range=[1.1, 1.4]  
    - 6 : [0.920] b3 zoom_range=[1.1, 1.5] brightness_range=[0.7, 1.0] rotation_range=0.2  
    - 7 : [0.921] b3 zoom_range=[1.0, 1.4] brightness_range=[0.7, 1.0] rotation_range=0.2   
    - 8 : [0.000] b4 zoom_range=[1.0, 1.3] brightness_range=[0.7, 1.0]   
- train_ext_data_06_5_14
    - _ : [0.000] b1 