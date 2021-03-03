# DL-DIY potential project ideas
- use pre-trained CLIP model on a different dataset for testing its potential for retrieval, e.g. Oxford Buildings (scripts for downloading data [here](https://github.com/filipradenovic/cnnimageretrieval-pytorch))
- use pre-trained CLIP in a zero-shot setting on an image dataset with some textual descriptions for images, e.g. dataset of paintings from a museum. Test out the performance. You can watch the first minutes of [this video](https://www.youtube.com/watch?v=T9XSU0pKX2E) to get an idea of the zero-shot setting here.

-----------------

# CLIP

[[Blog]](https://openai.com/blog/clip/) [[Paper]](https://cdn.openai.com/papers/Learning_Transferable_Visual_Models_From_Natural_Language_Supervision.pdf) [[Model Card]](model-card.md) [[Colab]](https://colab.research.google.com/github/openai/clip/blob/master/notebooks/Interacting_with_CLIP.ipynb)

CLIP (Contrastive Language-Image Pre-Training) is a neural network trained on a variety of (image, text) pairs. It can be instructed in natural language to predict the most relevant text snippet, given an image, without directly optimizing for the task, similarly to the zero-shot capabilities of GPT-2 and 3. We found CLIP matches the performance of the original ResNet50 on ImageNet “zero-shot” without using any of the original 1.28M labeled examples, overcoming several major challenges in computer vision.



## Approach

![CLIP](CLIP.png)

# ArtMining on the Brueghel dataset http://imagine.enpc.fr/~shenx/ArtMiner/
- in this paper they show how you can use some learned local features to discover recurring patterns in art images
- it would be interesting to see how well CLIP features would do here
- the idea here would be to extract features from some large image patches (you can do the cropping on the last feature map before transformers), multiple overlapping patches per image (you can use a sampling like in the R-MAC paper I mentioned in the last video), and to a nearest-neighbor search over the entire dataset and see what you retrieve
- no need to go in the same depth of exploration as the ArtMiner paper  (http://imagine.enpc.fr/~shenx/ArtMiner/visualRes/canaletto/canaletto.html)


# Recognizing objects in paintings
- https://www.robots.ox.ac.uk/~vgg/data/paintings/
- we could cast this as a retrieval setting, as you did with Oxford buildings: i.e. extract visual features for all images and then to nearest-neighbor search (don't forget to L2-normalize the features)
