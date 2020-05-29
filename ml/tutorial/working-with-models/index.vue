<script>
  export default {
    layout: 'training',
    title: 'Working with Models',
    tags: null,
    tldr: [
      'Purpose of models is to classify or predict data using algorithms'
    ]
  }
</script>

<template lang="md">

  20 years ago, it was pretty clear which types of work a computer could do better than a human. Anything involving number crunching with lots of data and quick turn around would be a great task to run on a computer. On the other hand, what if you wanted to save pictures from your island vacation and select the best ones to remember the trip by? You would have gone through hundreds of pictures individually to pick out the keepers. Smiling family, beautiful scenery, and action would be considered while blurry pictures and duplicates would be removed. Surely this would have been too subjective for a computer to weigh in.

  Fast forward to today. The best vacation pictures you want to keep probably share _some_ features with the millions of other pictures that are being taken. Why don't we tell a computer what to look for and it can do the work for us?

<img class="col-md-12" src="./imgs/picture-evaluation-checkmarks.png" /><br>

  ## Types of machine learning and some new terminology 

  If we are going to train a computer to be a good judge of vacation photos, we will have to be able to describe this in a way that it understands. A program with a bunch of _if_/_else_ statements are not going to serve us well here. What we need is a **model**, and not the runway walking variety!

  A model is an algorithm that can take input and predict what the output represents. It does this based on **features**, representing characteristics we have deemed important to distinguish good photos from bad. The predictions it gives are **labels** that describe the output in terms of our machine learning goals. In this case, it would be 'good vacation photo' or 'bad vacation photo'. If our goal is to label pictures in a way that is better than average, these general labels might be enough &mdash; most likely, however, we will want to be _approximately correct_ with what a family member would select from the vacation. In this case, more specific **labels** would be used.

  Determining what the model should look like follows the paths of **supervised** learning and **unsupervised** learning. The former, **supervised learning**, is when we act as the teacher showing the signals for correct output. In our example, this would mean providing photos that are _labeled_ correctly with what the computer should be able to predict once trained. **Unsupervised learning** will look at the data without any guidance and instead will come back with patterns that are recognized. There are tradeoffs with both techniques but with _machine learning_, supervised learning is preferred when possible.

  Let's use some visualization to drive this terminology home.

  ## Supervised learning

  <br>
<div><img class="col-md-8" src="./imgs/supervised-clusters.png" /><div class="col-md-4"><ul><li ><em>Data points</em></li><li><em>Labels</em></li><li><em>Features</em></li><li><em>Separating hyper plane</em></li></ul></div></div><br clear="all" />
  
  While greatly simplified, the diagram above is the stuff hundreds of books and PHds are written about, so take note! Here a set of data points are grouped into two clouds. These are represented in a 2-dimensional space, which means each point has both an x1 and an x2.

  ### Mini quiz 1

  ```{.center}
    Can you determine what are the _labels_ in this diagram?

    Can you determine what are the _features_?
  ```

  ### Insights

  The model described above is performing classification. Note that the point clouds are color coded with two different label colors. Orange and green are the labels. The spacial dimensions where the points live represent the magnitude of selected features, x1 and x2. The purpose of building this model is to arrive at the heart of machine learning, which is the separating hyper plane drawn as a blue line. Using this it is easy to determine how to label data points based on which side of the line they land on.

  ## Using the model after training

  Now that the model has been trained, let's see what happens when a new data point arrives.

  <img class="col-md-8" src="./imgs/new-node-supervised-cluster.png" /><br>

  Here the grey dot represents a new data point where we don't know the label. By using the model, we can find which side of the line the point falls on and see it should be given the orange label.

  ## Unsupervised learning

  To compare unsupervised learning, we would have data points but there would be no labels given. This is represented below by making all the data points grey. The model would be trained to find patterns in the data and decide on what makes it interesting or related.

  <img class="col-md-8" src="./imgs/unsupervised-clusters.png" /><br>

  ## In practice

  Here are some examples of machine learning classifiers in each category:

  **Supervised Learning:** Decision Tree, Random Forest, Boosting, SVM, logistic regression

  **Unsupervised Learning:** K-means, mean shift, PCA, ICA

  ### Deep Learning

  Where does deep learning fit into this? Is it supervised, unsupervised, or something else altogether? Give that some thought.

  Deep Learning has classifiers and techniques that be used as _supervised_ Deep Learning and _unsupervised_ Deep Learning. There are even _semi-supervised_ learning strategies. We will get into deep learning in the following lesson. For now, it is enough to know that certain methods such as Convolutional Neural Networks (CNNs) are supervised, while others such as Auto-encoders are unsupervised..

  ## Selecting and evaluating features

  Developing the machine learning model involves the selection of features, and some examples will show why this is important. Imagine that the data points represent apples and oranges and that we select roundness and weight as features.

  <div><img class="col-md-8" src="./imgs/roundness-weight-features.png" /><div class="col-md-4"><img src="./imgs/apples-oranges.png"></div>What features would you choose for this data set?</div><br clear="all" />

  You can see that this feature selection is not very useful as it gives very little signal for determining if a fruit is an apple or an orange. What if instead we decide to classify based on shape and color?

  <img class="col-md-8" src="./imgs/shape-color-features.png" /><br clear="all" />

  We can see a much better determination of what feature tells us the type of fruit. The point clouds now lie cleanly on each side of the dividing line. The slope of the line tells us something about shape. It is nearly orthgonal with the axis for _color_, and parallel with _shape_. This tells us that shape is _not_ a good predictor of the type of fruit. Even if we shuffled the points along the _shape_ axis, they would still fall cleanly on the same side of the line.

  ## Exercise

  Load the data science docker and start Jupyter. Review the instructions to do this, if needed.

  We are going to work with a training dataset for determining malicious websites based on different criteria. <a href="https://drive.google.com/open?id=1wVJHxZu3-DZ75kosuLgIacNCNzblgNIS">Download the dataset</a>, and make it available to load in your docker. Do this by putting it in the directory from where you start the docker instance. This folder loads as the /srv mount path and then you can call `.read_csv('/srv/dataset.csv')`, in your python notebook to load it..

  <a href="https://drive.google.com/open?id=1gQimkKmOArypsEg-koDAIPTbtq3EOlTt">Here is a link</a> to a Jupyter notebook to see various summaries of this data, as well as discovering the _separating hyper plane_ between websites that are malicious, and those that are safe.

  This dataset and Jupyter notebook come from the Kaggle website. Read the description for the dataset <a href="https://www.kaggle.com/xwolf12/malicious-and-benign-websites/data#">as mentioned on the Kaggle project page</a>. This will give you a better idea of what the columns mean.

</template>

<style lang="less" scoped>
  .word-break-normal {
    word-break: normal;
  }
  .update {
    font-style: italic;
    font-family: Georgia, serif;
    margin-bottom: 2em;
    p {
      margin-bottom: 5px;
    }
    blockquote {
      margin: 12px 0;
    }
  }
</style>
