<template lang="md">

## The work of a data scientist for system operators

Working with data means a lot of time is spent gathering, cleaning, transforming, and analyzing data. In this ML course, we will be using Python to perform this work. The first tool we will become acqainted with is the pandas library. There is so much you can do with this library that it would be exhausting to cover it all. Therefore, the strategy we will use is to give a healthy tour of what you can accomplish and then circle back for more detail in later lessons as needed. This is a common strategy that will be used throughout these lessons in order to balance theory, new ideas, and best practices.

For those of you looking for more, A list of links at the end will provide great references, cheatsheets and intermediate exercises to push you at the pace you want to go.

## Basic concepts

There are two fundamental types to pandas with which you will want to become familiar.

__Series__

This data type is an enhancement to basic arrays and dictionaries that are already available in Python. In fact, you can consider a Series to be like a dictionary, combined with the power of another type, the NumPy array. Dictionaries are great because they can do fast lookup by key, while arrays are good at constraining and growing memory only as needed. They are also good for iteration over elements. The Series was built to fit both of these strengths. In addition, becuase it provides the functionality of a NumPy array, it is 'missing data aware' &mdash; something we will see later. This type is best for single-dimensional data.

```{.center}
# Here we create a Series and address it
# Notice that instead of using the term 'key', Series uses the term 'index' or 'label' instead.
import pandas as pd
top_speeds = pd.Series([35, 64, 55, 19], index=['pronghorn', 'cheetah', 'antelope', 'hippo'])
```

__DataFrame__

This data type is the multi-dimensional companion to Series, and can be thought of as rows and columns, with labels acting as column-headings. It is capable of handling multiple datatypes in the same structure. By using indicies that are labeled, it has a powerful ability to retrieve data.

  <div class="unminify">
    <CodeEditor :code="code1a" :options="options"></CodeEditor>
  </div>
</template>

<script>
  import * as _ from 'lodash';
  import CodeEditor from '~/components/CodeEditor.vue';
  var dedent = require('dedent-js');

  //let exampleCode1a = dedent(`
  //  import requests
  //  print('hello')
  //`)
  let exampleCode1a = dedent(`
import pandas as pd

team_birthdays = [
  ['Sally', 'Finance', '03/25/1993'],
  ['Jean', 'Engineer', '12/14/1990']
]

pd.DataFrame(team_birthdays)

# with index and column information
pd.DataFrame(team_birthdays, index=['sally', 'jean'], columns=['first_name', 'department', 'birthdate'])
`)
  export default {
    layout: 'training',
    title: 'Intro to Pandas',
    tags: null,
    tldr: [
      'The use of Series and DataFrame for data science',
      'Making use of different operations on DataFrame type'
    ],
    components: {
      CodeEditor 
    },
    data() {
      return {
        options: {
          tabSize: 2,
          mode: 'python',
          line: true,
          lineNumbers: true,
          lineWrapping: true,
          foldGutter: true,
          styleActiveLine: true
        },
        code1a: exampleCode1a
      }
    }
  }
</script>

<style lang="less" scoped>
  @import (reference) '~assets/site.less';

  table, th, td {
    border: 1px solid black;
  }
  tbody tr:nth-child(odd) {
    background: #eee;
  }
  th, td {
    padding: 0.4rem;
    /*border: 1px solid #ccc;*/
  }

  .unminify {
    font-family: @font-family-sans-serif2;
    .error {
      font-size: 14px;
    }
    header {
      display: flex;
      padding: 5px 10px;
      background-color: #f7f7f7;
      border-bottom: 1px solid #ddd;
      align-items: flex-end;
      font-size: 14px;
      .btn {
        font-size: 14px;
        border: 1px solid  #ccc;
      }
      .input-group {
        width: 1%;
        .input-group-addon {
          cursor: pointer;
          font-size: 14px;
          background-color: #eee;
        }
        &.disabled {
          .opacity(.65);
        }
        .dropdown-menu {
          font-size: 14px;
        }
      }
      a {
        cursor: pointer;
      }
      div {
        flex: 0 0 auto;
        margin-left: 20px;
      }
    }
  }

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

  p {
      text-indent: 0 !important;
  }
</style>
