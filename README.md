# CLIP

[[Blog]](https://openai.com/blog/clip/) [[Paper]](https://cdn.openai.com/papers/Learning_Transferable_Visual_Models_From_Natural_Language_Supervision.pdf) [[Model Card]](model-card.md) [[Colab]](https://colab.research.google.com/github/openai/clip/blob/master/notebooks/Interacting_with_CLIP.ipynb)

CLIP (Contrastive Language-Image Pre-Training) is a neural network trained on a variety of (image, text) pairs. It can be instructed in natural language to predict the most relevant text snippet, given an image, without directly optimizing for the task, similarly to the zero-shot capabilities of GPT-2 and 3. We found CLIP matches the performance of the original ResNet50 on ImageNet “zero-shot” without using any of the original 1.28M labeled examples, overcoming several major challenges in computer vision.

## Approach

![CLIP](CLIP.png)

## I : Image Retrieval and Ranking
#### 1\ Brueghel Paintings Dataset 
Source: http://imagine.enpc.fr/~shenx/ArtMiner/

Objective: Extract features from the paintings data (only using vision model of CLIP), then search for the similar images within the dataset, using distance metric (Euclidean) or cosine similarity.

**Experiment I:**
      - Features retrieval using only the first convolutional layer of Visual network of ViT Clip Model.
      
       [X] L2 normalization -> Max-pooling -> Normalization.                 [X] L2 normalization -> Regional-Max pooling -> L2 Normalization.

**Experiment II:**
      - Features retrieval using only the first 3 convolutional layer of Visual network of ResNet50  Clip Model.
      
       [X] L2 normalization -> Max-pooling -> Normalization.                [X] L2 normalization -> Regional-Max pooling -> L2 Normalization.

**Experiment III:** In order to improve the retrieval process, since the pooling did not work very well. We used the following method

       [X] Extract Features from first conv1 layer (786 feature vectors) -> L2 normalization -> Regional-Max pooling -> L2 Normalization.
            
       [X] Extract Features from first conv1 layer (512 feature vector) -> PCA (512  ->> 100) -> K-Means Clustering (32 Cluster).

#### 2\ Oxford Buildings Dataset
Source: https://www.robots.ox.ac.uk/~vgg/data/paintings/

**Experiment I:**
      - Features retrieval using only the first convolutional layer of Visual network of ViT Clip Model.
      
        [X] L2 normalization -> Max-pooling -> Normalization.            [X] L2 normalization -> Regional-Max pooling -> L2 Normalization.

**Experiment II:**
      - Features retrieval using only the first 3 convolutional layer of Visual network of ResNet50  Clip Model.
      
        [X] L2 normalization -> Max-pooling -> Normalization.           [X] L2 normalization -> Regional-Max pooling -> L2 Normalization.

**Experiment III:** In order to improve the retrieval process, since the pooling did not work very well. We used the following method

        [X] Extract Features from first conv1 layer (786 feature vectors) -> L2 normalization -> Regional-Max pooling -> L2 Normalization.
            
        [X] Extract Features from first conv1 layer (512 feature vector) -> PCA (512  ->> 100) -> K-Means Clustering (10 Cluster).

## II: Zero-Shot learning:
#### 1\ Oxford Buildings Dataset

#### 2\ Emotion Dataset





