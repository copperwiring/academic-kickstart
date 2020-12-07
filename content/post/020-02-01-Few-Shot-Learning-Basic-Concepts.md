---
layout: post
title: "Few Shot Learning"
date: 2020-02-01 12:38:00 -0700
comments: true
tags: technical
# draft: true
---
<b>Question</b>: If a class has only two samples, can a computer make correct prediction? <br>
<i>Note: Number of samples is too less for training.</i>

<b>Approach:</b> Few Shot Learning

Few shot learning is a problem where we try to learn when the training data is very small. It is different from supervised learning where we train on some data and try to predict an object which belongs to a class present in training data. In few shot learning, the training data has never the sample we are predicting on.

Le's take an example. Look at Fig.1 

<figure>
    <img src="/img/half-training-data.jpg" width="300" height="400" />
    <figcaption>
    <a href="https://cs231n.github.io/classification/"> Fig 1. Photo via CS231 course</a>
    </figcaption> 
 </figure>

We train a model of a big training set of cats, dogs, mug and hat. The goal in few shot learning is not to recognize unseen cats/dogs/mugs/hats. Instead the goal is to recognize the similarity and difference between objects. After training, if we show two pairs of images (Fig.2 and Fig.3) to the model and ask "*Are the two images similar?*". 

<!DOCTYPE html>
<html>
<head>
<style>
* {
  box-sizing: border-box;
}
.column img {
    width: 100px;
    height: 150px;
    float: left ;
    padding: 10px; 
}
/* Clearfix (clear floats) */
.row::after {
  content: "";
  clear: both;
  display: table;
}
</style>
</head>
<body>
<div class="row">
    <div class="column">
        <img src="/img/cat.png" width="300" height="600" style="width:120%">
        <figcaption>
            <a href="https://medium.com/fenwicks/tutorial-4-demystifying-keras-dogs-vs-cats-tutorial-f7c5ea7adcf8"> Fig 2. Photo via Medium blog</a>
        </figcaption> 
    </div>
    <div class="column">
        <img src="/img/cat-dog.jpeg" width="300" height="600" style="width:100%" >
        <figcaption>
            <a href="https://cdn-images-1.medium.com/max/1600/1*EvMbMNRHm_aOf1n4tDO1Xg.jpeg"> Fig 3. Photo via Medium blog</a>
        </figcaption>  
    </div>
</div>
</body>
</html>

Since the model has learned the similarity and difference between objects, it can tell that images in Fig.2 are same kind of objects and Fig.3 are quite different. Now, if you ask the model to *recognize* the objects, it does not know it is cat or dog because it isn't a part of the training data.  Hence, model can tell that these two images are similar but can't tell what they are.

Now, let's ask another question. Let's ask the model what is Fig. 4. We call this image: **Query**

<figure>
    <img src="/img/squirrel.jpg" width="300" height="400" />
    <figcaption>
    <a href="http://weknowyourdreams.com/single/squirrel/squirrel-09"> Fig 4. "Query" (Photo via web)</a>
    </figcaption> 
 </figure>

Model is unable to answer this question because it has never seen this data during training. Now, I show another 4 images to the model as shown in Fig. 5

<figure>
    <img src="/img/support-set.png" width="600" height="800" />
    <figcaption>
    <a> Fig 5. "Support-Set"</a>
    </figcaption> 
 </figure>

 Now, model compares the query image with each image in the support set and believes the query is "Squirre". These set of labelled images are called **"Support Set"**.

-----

Jargons related to few-shot learning
<!-- Let's define few terms before we get into more technical details: -->

- <b>k-way:</b> we are given $j$ classes (e.g. 3-way means 3 classes. See Fig.1)
- <b>n-shot:</b> the number of samples per class (e.g. 2-shot mean 2 sample per class. See Fig.3)
- <b>Support set($S$):</b> the samples used for learning. If we have $j$ classes and $k$ samples, then number of elements in support set is $ j * k $.
- <b>Query set ($Q$):</b> the sample(s) which we are trying to identify.

<figure>
    <img src="/img/support_query.png " width="600" height="800" />
    <figcaption>
    <a href="https://www.borealisai.com/en/blog/tutorial-2-few-shot-learning-and-meta-learning-i/"> Fig 3. Photo via Borealis AI blog</a>
    </figcaption> 
 </figure>

More formally,if we define task with $T$, then task $T_i$ is sampled from probabilty distribution over tasks

<div> $$ T_i\sim P(T) $$</div>  and each task $i$ is a set given by Support $S$ and Query $Q$

<div>$$ T_i = \{ S_i, Q_i \} $$</div>

<!-- Points:
- If we already already pre-trained network on say,imagnet, it appears that if we simply use 'traditional' transfer learning, we shold be able to achieve  better results in j-way k-shot learning. However, it doesn't necessarily happen. <br /> <br />
We are dealing with domain transfer. First, there is the problem of domain shift. You may be in a new setting where your model cannot generalize to the new classes (classes different from the one in ImageNet for instance). Few-Shot models better deal with this setting. Second issue, in transfer learning you have to retrain part of the model (e.g. the last layer) and to do so you have to find the right number of epochs, optimizer, and hyperparams. This is very complicated to do when you have just a handful of data like in the Few-Shot setting. -->


