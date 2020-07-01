# SIIM-ISIC-Melanoma-Classification
Identify melanoma in lesion images  
Framework : Tensorflow / Keras  
Evaluate Metric : AUC
### Point
- Very HIGH class imbalance
 

## Base architecture
- Keras
- efficientnet ensemble by input size and network
- adam optimizer  


## Solutions  
- focal loss  
- over and under sampling - (undersampling)  
- augmentation  
  * ~~rotation_range~~
  * ~~rotate 90 = True~~
  * width_shift_range=0.2
  * height_shift_range=0.2
  * vertical_flip=True
  * horizontal_flip=True
  * zoom_range=[1.0, 1.3]
  * brightness_range=[0.7, 1.0]
  * ~~random_erase~~
- ensemble
  * k fold (k=5)
  * variety input size (224, 256, 512, 1024)
  * variety network (b0, b1, b2, b3, b4, b5)
  * ~~with rank data~~
- ~~weight balancing~~
  * Must not use 'focal loss' and 'weight balancing' together
- noisy-student (from check point)
  * stochastic depth
  * dropout
  * rand augment


## Result
- train_ext_data_06_5_9
    - _ : [0.921] b2 zoom_range=[1.0, 1.3]    
    - >1 : [0.922] b2 zoom_range=[1.0, 1.3] brightness_range=[0.7, 1.0] epoch15
    - 2 : [0.907] b2 zoom_range=[1.0, 1.3] brightness_range=[0.7, 1.0] epoch10
    - 3 : [0.890] b2 zoom_range=[1.0, 1.4] brightness_range=[0.7, 1.0] epoch13
    - 4 : [0.908] b2 zoom_range=[1.0, 1.3] brightness_range=[0.7, 1.0] epoch11
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
    - 8 : [0.912] b4 zoom_range=[1.0, 1.3] brightness_range=[0.7, 1.0]   
- train_ext_data_06_5_20
    - 224 * 224   
    - _ : [0.920] b4 zoom_range=[1.0, 1.3] 
    - _ : [0.000] b4 zoom_range=[1.0, 1.3] brightness_range=[0.7, 1.0]   
    
- train_ext_data_06_5_14
    - _ : [0.919] b1 zoom_range=[1.0, 1.3] brightness_range=[0.7, 1.1]
    - 1 : [0.913] b1 zoom_range=[1.0, 1.3] brightness_range=[0.7, 1.1] channel_shift_range=150.0

- train_ext_data_06_5_15
    - _ : [0.920] b5 zoom_range=[1.1, 1.4] brightness_range=[0.7, 1.0]
    - 1 : [0.922] b5 zoom_range=[1.0, 1.4] brightness_range=[0.7, 1.1]

- train_ext_data_06_5_16
    - 512 * 512
    - _ : [0.885] b0 zoom_range=[1.0, 1.3] brightness_range=[0.7, 1.1] batch8
    - 1 : [0.890] b0 zoom_range=[1.0, 1.3] brightness_range=[0.7, 1.1] batch16
    - 2 : [0.891] b0 zoom_range=[1.0, 1.3] brightness_range=[0.7, 1.1] channel_shift_range=150.0 batch16
    - 3 : [0.886] b0 zoom_range=[1.0, 1.3] brightness_range=[0.7, 1.1] rotation_range=10 batch16 step14
    - 4 : [0.894] b0 zoom_range=[1.0, 1.3] brightness_range=[0.7, 1.1] batch16 0data15000
- train_ext_data_06_5_18
    - 224 * 224   
    - _ : [0.908] b0 zoom_range=[1.0, 1.3] brightness_range=[0.7, 1.1] batch16 0data15000
    - 1 : [0.905] b0 zoom_range=[1.0, 1.3] brightness_range=[0.7, 1.1] batch16 0data20000 step11
    - 2 : [0.887] b0 zoom_range=[1.1, 1.4] brightness_range=[0.7, 1.2] batch16 0data20000 step15
    - 3 : [0.896] b0 zoom_range=[1.0, 1.3] brightness_range=[0.7, 1.1] shift_range=0.25 batch16 0data20000 step15     
    - 4 : [0.894] b0 zoom_range=[1.0, 1.3] brightness_range=[0.7, 1.1] shift_range=0.25 batch32 0data20000 step10     
    - 5 : [0.890] b0 albumentation   

- train_ext_data_06_5_17
    - 512 * 512
    - _ : [0.771] b6 zoom_range=[1.1, 1.4] brightness_range=[0.7, 1.0] batch2
    - 224 * 224
    - 1 : [0.890] b6 zoom_range=[1.1, 1.4] brightness_range=[0.7, 1.0] batch4

    
  
## Ensemble Result  
- [0.942] submission_ensemble_ext_data_06_5_9_1__06_5_13_2__4__7__06_5_14_0__06_5_15_0.csv
    - submission_ext_data_06_5_9_1
    - submission_ext_data_06_5_13_2
    - submission_ext_data_06_5_13_4
    - submission_ext_data_06_5_13_7
    - submission_ext_data_06_5_14
    - submission_ext_data_06_5_15

- [0.939] submission_ensemble_ext_data_06_5_9_1__06_5_13_2__4__7__06_5_14_0__06_5_15_0__06_5_16_2.csv
    - 7

- [0.939] submission_ensemble_ext_data_06_5_9_1__06_5_13_2__4__7__06_5_14_0__06_5_15_0__06_5_16_4.csv
    - 7

- [0.943] submission_ensemble_ext_data_06_5_9_1__06_5_13_2__4__7__06_5_14_0__06_5_15_0__06_5_18_0.csv
    - submission_ext_data_06_5_9_1
    - submission_ext_data_06_5_13_2
    - submission_ext_data_06_5_13_4
    - submission_ext_data_06_5_13_7
    - submission_ext_data_06_5_14
    - submission_ext_data_06_5_15
    - submission_ext_data_06_5_18

- [0.942] submission_ensemble_ext_data_06_5_9_1__06_5_13_0__2__4__06_5_14_0__06_5_15_1__06_5_18_0.csv
    - submission_ext_data_06_5_9_1
    - submission_ext_data_06_5_13
    - submission_ext_data_06_5_13_2
    - submission_ext_data_06_5_13_4
    - submission_ext_data_06_5_14
    - submission_ext_data_06_5_15_1
    - submission_ext_data_06_5_18
    
- [0.942] submission_ensemble_ext_data_06_5_9_1__06_5_13_0__2__4__06_5_14_0__06_5_15_1__06_5_18_0.csv
    - submission_ext_data_06_5_9_1
    - submission_ext_data_06_5_13_2
    - submission_ext_data_06_5_13_4
    - submission_ext_data_06_5_13_7
    - submission_ext_data_06_5_14
    - submission_ext_data_06_5_15_1
    - submission_ext_data_06_5_18
    
- [0.942] submission_ensemble_ext_data_06_5_9_0__1__06_5_13_0__2__4__7__06_5_14_0__06_5_15_1__06_5_18_0.csv
    - submission_ext_data_06_5_9
    - submission_ext_data_06_5_9_1
    - submission_ext_data_06_5_13_2
    - submission_ext_data_06_5_13_4
    - submission_ext_data_06_5_13_7
    - submission_ext_data_06_5_14
    - submission_ext_data_06_5_15_1
    - submission_ext_data_06_5_18
    - submission_ext_data_06_5_13