<template lang="md">

## Using Data Science as a System Operator

Gaining new insight from data means lots of time spent gathering, cleaning, transforming, and analyzing large data sets. In this ML course, we will be using Python to perform this work. The first tool we will become acqainted with is the pandas library. There is so much you can do with this library that it would be exhausting to cover it all. Therefore, the strategy we will use is to give a healthy tour of what you can accomplish and then circle back for more detail in later lessons as needed. This is a common strategy that will be used throughout these lessons in order to balance theory, new ideas, and best practices.

For those of you seeking maximum proficiency, A list of links at the end will provide great references, cheatsheets and intermediate exercises to push you at the pace you want to go.

## Basic concepts

There are two fundamental collection data types in pandas with which you will want to become familiar.

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

## Retrieving Data

Once the data is loaded into one of these collections, you are able to pull it out in one of many ways. In a DataFrame, each column uses the Series data type. When you request the data by column name, this Series is returned.

```{.center}
# This will return a Series of all departments that can be looked up/indexed by 
# user name, i.e. 'jdoyle'
depts = indexed_team_bday_df['department']
```

These can also be returned by label using the `loc` property.

```{.center}
# In this case it will return a Series for the row that has the value where the
# labels are set to the column names for that returned row.
user_jean = indexed_team_bday_df.loc['jdoyle']

# Both label and column name can be used to get the value for that exact location
user_jean_birthday = indexed_team_bday_df.loc[jdoyle', 'birthday']
```

Slicing shows The power of selective data retrieval. By using the python ':' subset operator, we can provide a range of values.

```{.center}
# This returns all rows and the selected columns as a list
indexed_team_bday_df.loc[:,['department', 'last_name']]
```

## Important properties and methods for data science

`.iloc()` and `.loc()`
Both of these seem to have some overlap in returning rows given an index or range of indices. So why are they named slightly different? This is because `.iloc()` uses the 0-based indexing used by the Python stdlib, while `.loc()` is _inclusive_. For string based ranges, it will usually be easier to use `.loc()`. Integer ranges may be either, but be careful or you will have off-by-one errors!

`.shape`
This is a property that returns a tuple describing the number of rows and columns for the DataFrame.

`.dropna()`
`.fillna()`
`.isnull()`
Because Series and DataFrame are missing data aware as mentioned ealier, these methods are available to select, replace (also known as 'impute'), or remove data based on missing values in any columns.

## Exercises

Load the data science docker and start Jupyter. See [previous lesson for info on setting this up](http://datacentric.blog/ml/tutorial/data-science-intro-and-materials).

1) Create a comma separated value file for members of your family and friend circle with _(a)_ their favorite movie and _(b)_ favorite food/candy. Decide if you want a header in the file.

2) Load this file into your docker and start a new notebook. The instructions to start docker have you map the local directory to _/srv/_ which you can use to bring files into docker.

3) Create a DataFrame from this and either create it with column names, or else it will infer the headers from the first row consumed.

4) Retrieve the list (Series) of favorite candy. These will be labeled by each person's name if you used an index, or incrementing number otherwise.

5) What is the shape of your DataFrame? Recall what this means from previous section. It will be (_no. of rows_, _no. of columns_) which is known as a 2-tuple.<br>
5a. How would the shape change if you decide to also track another dimension in your DataFrame, such as 'hometown'?<br>
5b. _**Optional** This will help you understand tensors later on, but for now is theoretical._<br>
Is it possible to have a shape described by a 3-tuple? What would this require in how your DataFrame is structured.<br>
_**Hint:**_ Recall that by using index, you have a lookup into a row. A second lookup by dimension name lets you also get the specific column. Would just adding a dimension give you shape described by a 3-tuple?<br>
_**Second hint:**_ An example is helpful.. think of how a Photoshopped image of a lawn can selectively apply a green mask to make the grass look more vivid. It will look at pixel intensity for each coordinate and additionally by Green intensity. 'Color' is another level of indexing into the collection of pixels.

6) Slice the DataFrame to return a subset of data based on column value.<br>
6a. For extra style points, do this based on either two or more columns, or column _and_ index. (Your choice)

## Further exercises

The easiest way to get additional tutorials and exercises is to go to [the Kaggle pandas module](https://www.kaggle.com/learn/pandas), read the tutorials and do the associated exercises. You only need to log in if you want to save work, or if you want to avoid the 5-10 minute idle timeout on workbooks.

With the same Docker, you can work through some of the exercises available [in this github project](https://github.com/treehouse-projects/python-introducing-pandas).

## Cheatsheets
[Pandas Cheatsheet](https://www.kaggle.com/grroverpr/pandas-cheatsheet)<br>
[Pandas and Dates Cheatsheet](https://www.kaggle.com/raenish/cheatsheet-date-helpers)

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
  ['Sally', 'Ferguson', 'Finance', '03/25/1993'],
  ['Jean', 'Doyle', 'Engineer', '12/14/1990'],
  ['Henry', 'Allison', 'Marketing', '01/16/1988']
]

# This creates the columns and rows, but no column names or indices (aka labels)
team_bday_df = pd.DataFrame(team_birthdays)

# Now try again with index and column information
indexed_team_bday_df = pd.DataFrame(team_birthdays, index=['sferguson', 'jdoyle', 'hallison'], columns=['first_name', 'last_name', 'department', 'birthdate'])
`)
  export default {
    layout: 'training',
    title: 'Intro to Pandas',
    tags: null,
    tldr: [
      'Understanding of Series and DataFrame collection types for data science work',
      'Practice with pandas data types (especially DataFrame!) which is widely used in ML'
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
