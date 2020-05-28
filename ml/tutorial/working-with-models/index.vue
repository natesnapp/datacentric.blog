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

  20 years ago, it was pretty clear which types of work a computer could do better than a human. Anything involving number crunching with lots of data and quick turn around would be a great task to run on a computer. On the other hand, what if you wanted to save pictures from your island vacation and select the best ones to remember the trip by? You would have gone through hundreds of pictures individually and to pick out the keepers. Smiling family, beautiful scenery, and action would be deteremined while blurry pictures and duplicates would be removed. Surely this would have been too subjective for a computer to weigh in.

  Fast forward to today. The good vacation pictures you want to keep probably share _some_ features with the millions of other pictures that are being taken. Why don't we tell a computer what to look for and it can do the work for us?

<img class="col-md-12" src="./imgs/picture-evaluation-checkmarks.png" /><br>

  ## Types of machine learning and some new terminology 

  If we are going to train a computer to be a good judge of vacation photos, we will have to be able to describe this in a way that it understands. A program with a bunch of _if_/_else_ statements are not going to serve us well here. What we need is a **model**, and not the runway walking variety!

  A model is an algorithm that can take input and predict what the output represents. It does this based on **features**, representing characteristics we have deemed important to distinguish good photos from bad. The predictions it gives are **labels** that descript the output in terms of our machine learning goals. In this case, it would be 'good vacation photo' or 'bad vacation photo'. If our goal is to label pictures in a way that is better than average, these general labels might be enough &mdash; most likely, however, we will want to be _approximately correct_ with what a family member would select from the vacation. In this case, more specific **labels** would be used.

  Determining what the model should look like follows the paths of **supervised** learning and **unsupervised** learning. The former, **supervised learning**, is when we act as the teacher showing the signals for correct output. In our example, this would mean providing photos that are _labeled_ correctly with what the computer should be able to predict once trained. **Unsupervised learning** will look at the data without any guidance and instead will come back with patterns that are recognized. There are tradeoffs with both techniques but often supervised learning is preferred when possible.

  Let's use some visualization to drive this terminology home.

  ## Supervised learning

  <br>
<div><img class="col-md-8" src="./imgs/supervised-clusters.png" /><div class="col-md-4"><ul><li ><em>Data points</em></li><li><em>Labels</em></li><li><em>Features</em></li></ul></div></div><br clear="all" />
  
  While greatly simplified, the diagram above shows what books and PHds are written about, so take note! The set of data points above are grouped into two clouds. These are represented in a 2-dimensional space, which means each point has both an x1 and an x2.

  ### Mini quiz 1

  ```{.center}
    Can you determine what are the _labels_ in this diagram?

    Can you determine what are the _features_?
  ```

  ## Unsupervised learning

  ## (In progress - Will add remainder today, May 28)

  This tutorial will cover how ML models work, and how to derive them from data
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
