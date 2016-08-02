Tweet Analytics with R
================

#### a template for exploring and analyzing tweet data from analytics.twitter.com

Twitter provides you with a list of all tweets you tweeted, together with more than forty metrics about each tweet; impressions, clicks, engagements, etc.

This is an rmarkdown template presentation, that serves as a starting point in analyzing your tweet activity and its results.

Since this report is the same for any account, and for any time period, I thought it makes sense to standardize the process because I often use it.

Suggested workflow:

1.  Download the file either from:
    [Twitter analytics](http://analytics.twitter.com) (click on the **Tweets** tab) *OR*
    [Twitter ads](http://ads.twitter.com) (Analytics --&gt;&gt; Tweet Activity)
2.  Add the path of the downloaded file as a `param` at the top of this report
3.  Add the most important keywords as another `param` at the top of the report
4.  Knit in your favorite format
5.  Analyze, edit, present, or take action

The main thing you will need to do is replace the path `"~/path/to/your/file.csv"` with the path of the downlaoded file, then add the most imoprtant keywords by replacing the second parameter `c("enter", "your", "most", "important", "words")`

YAML header where you need to modify `params`:

``` r
---
title: "Tweet Analysis"
author: "Your Name"
date: "Enter Date Here"
output:
  revealjs::revealjs_presentation: default
  ioslides_presentation: default
  beamer_presentation: default
  slidy_presentation: default
params:
  file: "~/path/to/your/file.csv"
  words: !r c("enter", "your", "most", "important", "words")
---
```

The `words` parameter should be the most important keywords that describe your Twitter account and the target topics and industry.

Once you enter those, they will be used as input in code chunks that will extract and analyze your usage of those keywords:
- Are these words used in enough tweets?
- Which of those words are you using the most?

Based on this, you can take action in terms of refocusing your content, and making sure you focus on the content that is most relevant to your audience.

#### Keep in mind

1.  The data is mainly about the tweets. Each row represents a tweet, together with all the available metrics. This means that you cannot determine how you are doing based on another dimension, days for example. In one of the slides, you will see some monthly metrics with the note that it is only an approximation

2.  This document is meant to be a starting point in your analysis of your tweet activity. There are more than forty columns, and the possible combinations are endless. I have chosen the main metrics that give an overview of:
    1.  tweet activity: daily, monthly, day of week, and hourly
    2.  word usage: all the words that are used, weighted and absolute frequency, together with the target words of your choice
    3.  hashtags and mentions: count, frequency, and the top ones that you are using

3.  Encoding might be an issue especially with emoticons, and if you are using different languages. A quick fix that works for English, is a line that converts the encoding of the tweets text. This is in the fist chunk, and you will simply have to uncomment the line
    \#tweets\_df$\`Tweet text\` &lt;- iconv(tweets\_df$`Tweet text`, "ASCII", "UTF-8", "byte")
    Sorry I'm not an expert on encoding and how you can solve these issues!

4.  Packages used are the following in case something acts funny:

| Package    | Version   | Remarks                                              |
|------------|-----------|------------------------------------------------------|
| knitr      | 1.13      |                                                      |
| readr      | 0.2.2     |                                                      |
| dplyr      | 0.5.0     |                                                      |
| lubridate  | 1.5.6     |                                                      |
| ggplot2    | 2.1.0     |                                                      |
| advertools | 0.0.0.900 | `devtools::install_github("eliasdabbas/advertools")` |
| DT         | 0.1.64    |                                                      |
| viridis    | 0.3.4     |                                                      |
