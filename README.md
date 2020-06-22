# SIIM-ISIC-Melanoma-Classification
Identify melanoma in lesion images
  
Very HIGH class imbalance.  


## Base architecture
1. efficientnet b0   
  or **efficientnet b2** is best in my source  
2. adam optimizer  


## Solutions  
1. focal loss  
2. over and under sampling - (undersampling)  
3. augmentation  
  - rotation_range=20 (90 is not working)
  - width_shift_range=0.2
  - height_shift_range=0.2
  - vertical_flip=True
  - horizontal_flip=True
4. ensemble (to do)
5. class weight (to do)      
   maybe not use with focal loss and class weight 
6. noisy-student 