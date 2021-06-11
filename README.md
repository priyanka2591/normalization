## Different types of Normalization <br>

#### Explanation of code

1) The model used here is the the model trained on the MNIT dataset for the prediction of the digits in the dataset
2) model.py file consists of three different models built using three different normalization techniques - Batch normalization, Layer normalization and Group normalization.
3) Three classes are defined inside the model.py file. 
4) Pytorch  nn module has been used to implement the <br>

    (a) BatchNorm2d() where batch normalization is done for each channel in a particular layer across all the batches. Hence the number of parameters used here would be 
    2 * number of channels (1 gamma and 1 beta for each channel across all imgaes of that particular layer in that batch)<br>
    
    (b) Layer normalization is done using GroupNorm(1, channels) -> which indicates that there is one group across all the channels and sonormalization is done across all 
    the channels in that particular layer of the image. hence there are only two paramters  here technically (1 gamma and 1 beta). This is done by using the function 
    Groupnorm(n_groups =1, n_channels)<br>
    
    (c) Group normalization is also done horizontally across all the channels in a layer which is divided into n groups. So if there are two groups (16 channels) there should be 
    two normalizations taking place (8 channels each) which each of it having 1 gamma and 1 beta. Thisis done by using the function Groupnorm(n_groups, n_channels)<br>
    
    The Pytorch documentation:<br>
    
    Unlike as mentioned above, Pytorch implements group normalization and layer normalization by having one gamma and one beta alloted for each of the channels. Hence the total number of paramters reamin the same for group layer and batch normalization as the gamma and beta are separate for each channel. However the normalization is done as per the 
    concepts.<br> 
    
      - Batchnormalization does normalization for each channel across batches for a particular layer. (Vertical)<br>
      - Layer normalization does normalization for all channels in a layer for an image. (Horizontal)<br>
      - Group normalization does normalization for a group of channels in a layer for an image (Horizontal)<br>
5) L1 loss is implemented in the training function and the l1 loss is added to the total loss before doing backpropogation or differentiation.<br>

#### Explanation of Excel sheet <br>

1) As mentioned above in case of Batch normalization, the values across all the channels (vertical) in a particular layer for all the images  in a batch are normalized and then the shift and scale is reapplied (Gamma and beta) for EACH CHANNEL. <br>

2) In case of layer normalization, the value across all the channels in a layer of a particular image are normalized amongst itself (horizontal). There will be one gamma and one beta 
