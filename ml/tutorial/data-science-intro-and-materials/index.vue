<script>
  export default {
    layout: 'training',
    title: 'Data Science introduction and materials',
    tags: null,
  }
</script>

<template lang="md">

  ## What is ML Training for Operators?

  In data science and ML the norm is for large quantities of data to flow into storage where insights are derived. Because of time and skillset, this often moves outside of the system operator domain and to individuals that are trained in statistical reasoning, data science, and machine learning. The single biggest difficulty faced by data minded teams today is to link advanced insights back into the operational side of house which provides the service.

  This goal of this training is to compare standard approaches such as prediction via linear regression and ARIMA and classification methods (such as logistic regression), with the latest advances in Machine Learning. This course will study random forests and neural networks and put it to use in practical ways to improve operations. The ability to dive in and gain insights by bright operation-oriented minds has never been better, given the readily available tools and instruction.

  ## Kick the tires and light some fires

  Hopefully you already have docker installed? If not, get it running. You only have a few steps and you are ready to go!

  Now get the datascience toolkit. This will give you access to Tensorflow, SciKit learn, Pandas, etc without having to set it all up yourself. With docker installed on your laptop, create a new directory where you will put new class files, and pull down and start the docker image and fire it up!
  
  Steps with example names:
  1. $> mkdir datascience
  2. $> cd datascience
  3. $> docker pull datacentric2/datacentric:1.0
  4. $> docker run -it -p 8888:8888 -u $(id -u):$(id -g) -v $(pwd):/srv datacentric2/datacentric:1.0
  5. Then open up a browser and go to the link it displays to see Jupyter
  example - you will have a unique token 
  http://127.0.0.1:8888/?token=2b5d53f669b996f0cdd10e9286f3362ee0de110e58834d41
  
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
