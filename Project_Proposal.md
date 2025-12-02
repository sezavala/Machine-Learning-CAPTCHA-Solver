# CST463 Project Proposal

## Team members
- Sergio Zavala
- Matthijs De Vries
- Jean-Luc Martel
- Alexis Guzman

## Project idea
CAPTCHA systems are always evolving to ensure safety from bot attacks. The issue our project addresses is to attempt to use a pretrained model to build a machine learning algorithm that can accurately predict the correct symbols from a CAPTCHA image. By attempting to crack CAPTCHA systems, we can identify flaws in current systems to include when planning future systems. 

- Baseline Goal: Since we are working with a pretrained model, our baseline goal is to improve the baseline accuracy by 5-10%
- Stretch Goal: Our stretch goal is to reach 10-20% accuracy improvement on unseen data.

## Data Set
The dataset we are using is the CAPTCHA Images dataset. The images are 5-letter words that can contain numbers. The photos have had noise applied to them (blur and a line), and they are 200 x 50 PNGs. This data set is built on 1070 images, which will need to be manipulated for accurate results.

## Architectures to utilize
Since we are working with images of letters and numbers combined, the most appropriate architecture to use is a 2D convolutional neural network. This would likely consist of an input layer -> convolutional layer -> pooling layer -> convolutional layer -> pooling layer -> flatten / dense layer. We would likely use softmax for our activation for the probability of our result.

We can also leverage a pre-trained model, like the VGG16 architecture, as recommended in the textbook. We can reuse the convolutional base since the features of a convnet are maps of generic concepts over a picture, which will be useful to have already. We will need to change the classification layer since it was likely trained for on different classes.

## Techniques to leverage
Some techniques we can leverage are:

- Data Augmentation: This is useful because we are working with a small dataset of ~1000 samples, and avoid overfitting.
- Reusing layer: As mentioned earlier, with a pretrained model, we can freeze base layers and switch the classification layer to take advantage of the pretrained weights and fine-tune that top layer.
- ADAM: To avoid falling into the local minimum, we can use an optimizer like Adam and potentially a learning rate scheduler.
- Multi-class: Since we are predicting 5 letters/numbers, this is classified as a multi-class classifier. We can leverage the one vs all or one vs one technique.
- Preprocess data: Since we are working with messy data, we need to prepare the images: convert to grayscale, resize, and normalize pixels.

## Expected Computational Requirements
Our project uses a pretrained CNN, and we only fine-tune the upper layers. This requires relatively little compute. Google Colab’s free GPU is more than enough for loading the pretrained model and training a small classification head. I read that fine-tuning can take 5–15 minutes per run, and our dataset is small, so memory and runtime demands stay low. We may need to augment more data using our existing data, but we also have personal GPUs we can fall back on. Therefore, Colab provides sufficient computational resources for the entire project.
