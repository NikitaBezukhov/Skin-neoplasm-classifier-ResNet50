# Skin neoplasm classification with ResNet50! (PyTorch)
####
## The data set is __[Skin Cancer MNIST: HAM10000 from Kaggle](https://www.kaggle.com/kmader/skin-cancer-mnist-ham10000)__.
## Was built in __[Google Colab](https://colab.research.google.com/)__ environment, so make any adjustments needed for it to work on your machine.
## You can find code and detailed project analysis in __[Skin_classifier.ipynb](https://github.com/NikitaBezukhov/Skin-neoplasm-classifier/blob/main/Skin_classifier.ipynb)__ notebook.
## The results of the training will be presented below.
### Dataset consists of 7470 unique neoplasm photos from 7 classes such as: 
#### 1. Melanocytic nevi
#### 2. Melanoma
#### 3. Benign keratosis-like lesions
#### 4. Basal cell carcinoma
#### 5. Actinic keratoses
#### 6. Vascular lesions
#### 7. Dermatofibroma
## Model was trained on 1 Tesla p100 GPU for 290 epochs (around 12 hours) with early stopping point at 240 epochs. Concervative early stopping patience of 50 epochs was chosen because dataset is greatly skewed and training with Random data augmentations was going pretty stochastically, but model was still slowly and steadily converging. 
## Resulting training metrics were:
![Train_results](https://user-images.githubusercontent.com/74721678/125439228-13fbbeea-8081-43e8-8a5e-7919460088a0.png)
![Tensor_board_curves](https://user-images.githubusercontent.com/74721678/125439235-2e1a0228-84e7-49e2-b021-b16227857e04.png)
![Metrics_1](https://user-images.githubusercontent.com/74721678/125443558-b572f2af-0df7-4e48-a32a-900bb733e378.png)
### For better validation robustness I spined validation data 5 times with random Horizontal flip (50% chance) and random Rotation (-180,180, 99% chance) and got next metrics:
![Metrics_2](https://user-images.githubusercontent.com/74721678/125444128-a0352855-0d4f-49d6-8b27-5e12279796ed.png)
## In the end we were able to achieve 97% average F1 score with all by class AUCs close to 100%! 
## And what is interesting, even on 2 classes with smallest representations (only 78 and 58 training images) we still were able to achieve 100 and 99% F1 score respectively.
## I believe that the most important reason for that good of a result were well chosen data augmentations that helped not only to enrich our dataset, but also prevent overfitting. 

