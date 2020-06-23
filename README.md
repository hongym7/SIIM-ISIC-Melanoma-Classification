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
  * rotation_range=20 (90 is not working)
  * width_shift_range=0.2
  * height_shift_range=0.2
  * vertical_flip=True
  * horizontal_flip=True
- ensemble (to do)
  * variety input size
- class weight (to do)      
  * maybe not use with focal loss and class weight 
- noisy-student 