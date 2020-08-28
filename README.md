# SIIM-ISIC-Melanoma-Classification
Identify melanoma in lesion images  
https://www.kaggle.com/c/siim-isic-melanoma-classification/overview  

### Point
- Very HIGH class imbalance

## Base
- Framework : Tensorflow / Keras  
- efficientnet ensemble by input size and network
- adam optimizer  
- Evaluate Metric : AUC


## Solutions  
- focal loss  
- over and under sampling  
- augmentation  
  * ~~rotation_range~~
  * ~~rotate 90 = True~~
  * width_shift_range=0.1
  * height_shift_range=0.1
  * vertical_flip=True
  * horizontal_flip=True
  * zoom_range=[1.0, 1.3]
  * brightness_range=[0.7, 1.0]
  * random_erase(cutout)
- ensemble
  * k fold (k=5)
  * variety input size (224, 256, 512, 768)
  * variety network (~~b0,~~ ~~b1~~, b2, b3, b4, b5, ~~b6~~)
  * rank ensemble (min, max, **avg**)
- ~~weight balancing~~
  * Must not use 'focal loss' and 'weight balancing' together
- noisy-student (from check point)
  * stochastic depth
  * dropout
  * rand augment
- TTA (test time augmentation) ensemble
  * original
  * vertical_flip
  * horizontal_flip


## Result  
- train_b1_256
    - 01 : [0.9106] zoom_range=[1.0, 1.1] brightness_range=[0.8, 1.1]
    - 02 : [0.9060] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]
- train_b1_384
    - 01 : [0.9170] zoom_range=[1.0, 1.1] brightness_range=[0.8, 1.1]
    - 02 : [0.9284] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]
- train_b1_512
    - 01 : [0.9080] zoom_range=[1.0, 1.1] brightness_range=[0.8, 1.1]
    - 02 : [0.9256] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]
- train_b1_768
    - 01 : [0.9255] zoom_range=[1.0, 1.1] brightness_range=[0.8, 1.1]    
    - 02 : [0.9134] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]



- train_b2_256
    - 01 : [0.9083] zoom_range=[1.0, 1.1] brightness_range=[0.8, 1.1]
    - 02 : [0.9281] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]
    - 03 : [0.9159] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1] shift_range=0.2
- train_b2_384
    - 01 : [0.9285] zoom_range=[1.0, 1.1] brightness_range=[0.8, 1.1]
    - 02 : [0.9311] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]
    - 03 : [0.9336] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1] shift_range=0.2
- train_b2_512
    - 01 : [0.9254] zoom_range=[1.0, 1.1] brightness_range=[0.8, 1.1]
    - 02 : [0.9401] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]
    - 03 : [0.9229] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1] shift_range=0.2
- train_b2_768
    - 01 : [0.9240] zoom_range=[1.0, 1.1] brightness_range=[0.8, 1.1]
    - 02 : [0.9314] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1] 
    - 03 : [0.9270] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1] shift_range=0.2
    - 05 : [0.9185] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1] 


- train_b3_192
    - 01 : [0.9096] zoom_range=[1.0, 1.1] brightness_range=[0.8, 1.1]
    - 02 : [0.9091] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]
    - 03 : [0.0000] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]
- train_b3_256
    - 01 : [0.9322] zoom_range=[1.0, 1.1] brightness_range=[0.8, 1.1]
    - 02 : [0.9217] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]
    - 03 : [0.9275] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]
    - 05 : [0.9351] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]
- train_b3_384
    - 01 : [0.9228] zoom_range=[1.0, 1.1] brightness_range=[0.8, 1.1]
    - 02 : [0.9313] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]  
    - 02' : [0.9296] inference resize   
    - 03 : [0.9354] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1] shift_range=0.2 
    - 05 : [0.9387] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]  
- train_b3_512
    - 01 : [0.9150] zoom_range=[1.0, 1.1] brightness_range=[0.8, 1.1]
    - 02 : [0.9316] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]   
    - 03 : [0.9263] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1] shift_range=0.2 
    - 04 : [0.9221] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]  
    - 05 : [0.9245] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]  
- train_b3_768
    - 01 : [0.9122] zoom_range=[1.0, 1.1] brightness_range=[0.8, 1.1] 
    - 02 : [0.9121] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]
    - 03 : [0.9044] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1] shift_range=0.2     
    - 05 : [0.9293] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1] 


- train_b4_192
    - 02 : [0.9033] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]
- train_b4_256
    - 01 : [0.9287] zoom_range=[1.0, 1.1] brightness_range=[0.8, 1.1]
    - 02 : [0.9358] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]
    - 03 : [0.9252] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1] shift_range=0.2
    - 05 : [0.9256] zoom_range=[1.0, 1.1] brightness_range=[0.8, 1.2]     
- train_b4_384
    - 01 : [0.9182] zoom_range=[1.1, 1.3] brightness_range=[0.8, 1.1]    
    - 02 : [0.9400] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]
    - 03 : [0.9359] zoom_range=[1.0, 1.1] brightness_range=[0.8, 1.1] shift_range=0.2
    - 03_02 : [0.9284] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1] shift_range=0.2
    - 05 : [0.9233] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]
- train_b4_512
    - 01 : [0.9302] zoom_range=[1.0, 1.1] brightness_range=[0.8, 1.1]
    - 02 : [0.9241] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]
    - 03 : [0.9319] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1] shift_range=0.2
    - 05 : [0.9267] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]
- train_b4_768
    - 01 : [0.8932] zoom_range=[1.0, 1.1] brightness_range=[0.8, 1.1]
    - 01' : [0.8661] more initial lr   
    - 02 : [0.8903] zoom_range=[1.0, 1.2] brightness_range=[0.8, 1.1]
    
  
## Ensemble Result  
  - [0.9516] submission_ensemble_011.csv
    - submission_b1_384_02-15step.csv
    - submission_b1_512_02-18step.csv
    - submission_b2_256_02-09step.csv
    - submission_b2_384_03-17step.csv
    - submission_b2_512_02-16step.csv
    - submission_b2_768_02-17step.csv
    - submission_b3_256_01-14step.csv
    - submission_b3_384_02-16step.csv
    - submission_b3_512_02-16step.csv
    - submission_b4_384_03-17step.csv
    - submission_b4_512_01-13step.csv
    
  - [0.9523] submission_ensemble_012.csv
    - submission_b1_512_02-18step.csv
    - submission_b2_256_02-09step.csv
    - submission_b2_384_03-17step.csv
    - submission_b2_512_02-16step.csv
    - submission_b2_768_02-17step.csv
    - submission_b3_256_01-14step.csv
    - submission_b3_384_02-16step.csv
    - submission_b3_512_02-16step.csv
    - submission_b4_384_03-17step.csv
    - submission_b4_512_03-15step.csv
 
