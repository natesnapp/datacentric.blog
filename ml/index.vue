<template>
  <div>
    <blog-card
      linkpage="ml/tutorial/data-science-intro-and-materials"
      name="Data Science introduction and materials"
      category="Getting started"
      image="ml/imgs/baby-bears.jpg"
      author=""
      desc="See the goals for this course and get a one-stop docker image to complete setup (hint: it's easy!)"
    ></blog-card>
    <blog-card
      linkpage="ml/tutorial/intro-to-pandas"
      name="Introduction to Pandas"
      category="Week 1-a"
      image="ml/imgs/frog-flower.jpg"
      author="Added on May 23"
      desc="Pandas is a popular library for data science work that provides a foundation through its data types, which you will learn about in this lesson."
    ></blog-card>
    <blog-card
      linkpage="ml/tutorial/working-with-models"
      name="Working with models"
      category="Week 1-b (COMING SOON)"
      image="ml/imgs/peeking-fawn.jpg"
      author="Adding on May 27"
      desc="In order to better work in data science, follow this training to become more familiar with how Pandas is used to work with Series and DataFrames"
    ></blog-card>
    <!--<CodeEditor :code="code" :options="options" @input="setCode" @focus="clear"></CodeEditor>-->
  </div>
</template>

<script>

// Load CSS from the local repo
//require("/Users/natesnapp/working/natesnapp/vue-simple-calendar/static/css/default.css")
//require("./calendar-theme.css")
//require("/Users/natesnapp/working/natesnapp/vue-simple-calendar/static/css/holidays-us.css")

  //import { formatDate } from '~/assets/dateUtils.js'
  import BlogCard from '~/components/BlogCard'
  import * as _ from 'lodash';
  //import CodeEditor from '~/components/CodeEditor.vue';

  //let exampleCode = "var Exported=(function c(w){var a='name';return w.component(a);})(Vue)";

  export default {
    title: 'ML Training for Operators',
    layout: 'training',
    components: {
        BlogCard //, CodeEditor
    },
    data() {
      return {
      }
    },
  }

</script>

<style lang="less" scoped>
  @import "../../assets/variables.less";

  .cv-week {
    flex-basis: 6em;
  }

  a {
    border-bottom: 0;
  }

  .page-preview {
    &:first-child {
      margin-top: 1em;
    }
    margin-bottom: 3.5em;

    header {
      h2 {
        font-size: 40px;
      }
    }

    footer {
      display: flex;
      color: @gray-light;
      font-size: .9em;
      font-family: @font-family-sans-serif2;
      font-weight: 300;
      p {
        margin-left: auto;
        padding-left: 20px;
        text-align: right;
        text-indent: 0;
        white-space: nowrap;
      }
    }

    .header-info {
      display: flex;
      justify-content: space-evenly;
      font-size: 1.2em;
      & > div {
        flex: 1 1 auto;
      }
      .date {
        /*padding-left: 20px;*/
        white-space: nowrap;
      }
      .tags {
        padding-left: 20px;
        justify-self: right;
      }
    }
  }

  html,
  body {
      height: 100%;
      margin: 0;
      background-color: #f7fcff;
  }
  p {
      text-indent: 0 !important;
  }
  #app {
      display: flex;
      flex-direction: row;
      font-family: Calibri, sans-serif;
      width: 95vw;
      min-width: 30rem;
      max-width: 100rem;
      min-height: 40rem;
      margin-left: auto;
      margin-right: auto;
  }
  .calendar-controls {
      margin-right: 1rem;
      min-width: 14rem;
      max-width: 14rem;
  }
  .calendar-parent {
      display: flex;
      flex-direction: column;
      flex-grow: 1;
      overflow-x: hidden;
      overflow-y: hidden;
      max-height: 100vh;
      background-color: white;
  }
  /* For long calendars, ensure each week gets sufficient height. The body of the calendar will scroll if needed */
  .cv-wrapper.period-month.periodCount-2 .cv-week,
  .cv-wrapper.period-month.periodCount-3 .cv-week,
  .cv-wrapper.period-year .cv-week {
      min-height: 8rem;
  }
  /* These styles are optional, to illustrate the flexbility of styling the calendar purely with CSS. */
  /* Add some styling for events tagged with the "birthday" class */
  .theme-default .cv-event.birthday {
      background-color: #e0f0e0;
      border-color: #d7e7d7;
  }
  .theme-default .cv-event.birthday::before {
      content: "\1F382"; /* Birthday cake */
      margin-right: 0.5em;
  }

</style>
