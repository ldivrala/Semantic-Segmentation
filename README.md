# Semantic Segmentation

Dataset :: [Semantic Segmentation for Self Driving Cars](https://www.kaggle.com/kumaresanmanickavelu/lyft-udacity-challenge "Semantic Segmentation for Self Driving Cars") \
Tools :: Tensorflow, Numpy, Pandas, Keras \
Architecture :: U-net


* Dataset :: 
  * This dataset provides data images and labeled semantic segmentations captured via CARLA self-driving car simulator. The data was generated as part of the Lyft Udacity Challenge.
  * The data set contains sets of RGB and the corresponding semantic segments.
  * The data has 5 sets of 1000 images and corresponding labels. We had used only one for training.

* Inspiration::
  * We have to find out diffrent classes in image and segment them in diffrent colors according to class probability.
  
  
![Unet Architecture](Unet%20Architecture_.png?raw=true "Unet")

  
### Steps (What we did) ::
  1. Create our dataset pipline (Tensorflow) :: Preprocessing image from image path, Cache, Batch, Shuffle (Dataset A).
  
  2. Convolution Block :: Conv2D (3, "same") -> Relu -> Conv2D (3, "same") -> Relu -> Dropout (Optional) -> MaxPooling.
  
  3. Upsampling Block  :: Conv2dTranspose (3, "same", 2) -> Concatenate ( Above 4th) -> Conv2D(3, "same") -> Relu -> Conv2D(3, "same") -> Relu

  4. Unet Model :: ConvBlock (32) -> ConvBlock (64) -> ConvBlock (128) -> ConvBlock (256) -> ConvBlock (512) -> Upsampling (256) -> Upsampling (128) -> Upsampling (64) -> Upsampling (32) -> Conv2d (32, 3, "same") -> Conv2d (#Classes, 1, "same")
  
  5. Model Training :: Adam Optimizer, SparseCategorical CrossEntropy Loss, 80 Epochs
  
  6. Testing on another dataset C.
  
  7. Loss, Accuracy = 0.1277, 0.9526

