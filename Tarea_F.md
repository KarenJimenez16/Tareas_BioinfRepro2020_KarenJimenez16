### Select random rows of a data set in `R`

Sometimes is necessary make a analysis with a little porcentage of the total of the data we have, this with the goal of check that every step and command used in our workflow runs correctly and effectly. It's a good idea to use random observations of our data for avoid bias for only use observations of the same population or specie. In this case, a important question is: "¿How to select random observations in our data set in `R`?". I searched for the answer of this question in Stack Overflow and I found [this answer.](https://stackoverflow.com/questions/8273313/sample-random-rows-in-dataframe)

The user `nikhil` ask: 
`I am struggling to find the appropriate function that would return a specified number of rows picked up randomly without replacement from a data frame in R language? Can anyone help me out?`

And the user `John Colby` answer this way: 

First make some data:
**This step is not necessary is we already have data and only want to select random observations or rows of it.** Here he create a data frame named `df`. Inside this data frame, we have twenty numbers of valors in normal distribution in ten rows.  
```
> df = data.frame(matrix(rnorm(20), nrow=10))
> df
           X1         X2
1   0.7091409 -1.4061361
2  -1.1334614 -0.1973846
3   2.3343391 -0.4385071
4  -0.9040278 -0.6593677
5   0.4180331 -1.2592415
6   0.7572246 -0.5463655
7  -0.8996483  0.4231117
8  -1.0356774 -0.1640883
9  -0.3983045  0.7157506
10 -0.9060305  2.3234110
```

Then select some rows at random:
**The answer of the question is here. We can use the `R` function `sample` for select a subset of a data frame. He use `df[~]` because it's a form to tell to `R` that we wanna use the function inside the square brackets in the objetc `df` created in the past step.
Inside the function `sample`, he use `nrow(df)` to tell `R` that we wanna select rows of the `df` data frame. Finally, he use `3` to only select three rows of the ten rows in the data frame. If we want to selet more rows, we only need to change the number three for the number of rows we want to select of our data.** 

```
> df[sample(nrow(df), 3), ]
           X1         X2
9  -0.3983045  0.7157506
2  -1.1334614 -0.1973846
10 -0.9060305  2.3234110
```
