# -Transfer_learning_Resnet34_and_NasNetMobile
Application of transfer training from different CNN models pre-trained on ImageNet to new image data


                  **Application of transfer learning from different pre-trained CNN models**
                  
 The task consists of the following steps:

1. The input images will be normalized to the average RGB plane of the
images from imageNet.
2. Apply an augmentation of the train data, with a horizontal flip.
3. Load a pre-trained model on ImageNet without the last FC layer
4. Make a model.summary() with and without the last layer in order to see the layer and redefine (a globalaveragepooling,
   a dropout, a flatten, etc) this differs from a template to each other.
5. Define a new FC layer identical to the old one (the structure of the FC layer. but this time it was randomly initialized.
   The number of output neurons is equal to the number of base classes to be processed, 
   the learning rate must be an a rather low value of 0.001.
6. Reconstruct the new model.
7. Do a fine-tuning on the new FC for a number of epochs, in order to to learn weights adapted to the new base. 
   Here the other layers are a priori all frozen.
8. After training the new FC, we will adapt the upper layers of the model to the new base in two ways:
    a) Freeze the first layer and fine-tuning the upper layers.
    b) Freeze the first two layers and fine-tuning the upper layers.
   Here the interest of fine-tuning a) and b) is to see the contribution of the transfer learning on a base of different
   from imageNet and the generalizability of the model.
9. Make a fine-tuning assessment of :
    a) The number of epochs
    b) Batch size
    c) Deterioration in the learning rate
         - Standard degradation of the learning rate
         - Programmed degradation of the learning rate
         - Step-by-step degradation
         - Polynomial degradation
-- This is based on the observation of loss/accuracy plots for different test values (e.g. define a batch size range of [8 16 32],
   an epoch range of [10 25 50 75 100 150], and finally different learning rate degradations.
-- At the end of this evaluation we will have the optimal values of the batch size, the number of epochs and
   the degradation of the learning rate that does not lead to overfitting.
-- This assessment is to be done for steps 7., 8.a) and 8.b).

 10. Once the optimal model has been found after the evaluation :
     e) Save the model.
     f) Save the learning history.
     g) Save the values of the performance measures: accuracy, recall/precision/F measure.
     h) Save loss/accuracy graphs.<br/>
 11. Use the learned model as a feature extractor :<br/>
     d) Load the optimal model from steps 7, 8.a), 8.b)<br/>
     e) Run through the base images and extract the descriptor vector of the last layerbefore CF.<br/>
     f) Save the descriptor vectors.<br/>
