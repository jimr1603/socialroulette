# socialroulette: A package to generate social groupings

A package for partitioning individuals into groups of a pre-specified size. This can be as simple as using simple random sampling (srs) to divide n individuals into groups of size at least m. If one keeps track of the past partitions then an additional
aim can be to try to maximize the time that people have a reunion, i.e. end up in the same group. This boils
down to an instance of the maximally diverse grouping problem.
See the [package website](https://hoehleatsu.github.io/socialroulette/)  for more information, documentation and examples. The package source code is available from [GitHub](https://github.com/hoehleatsu/socialroulette/).

```
# Install package
devtools::install_github("hoehleatsu/socialroulette")

# Distribute 5 ppl into 2 group of at least 2 using simple random sampling
frame <- tibble(id=sprintf("id%.3d", 1:5), date=Sys.Date())
rsocialroulette(frame, past_partitions=NULL, m=2, algorithm="srs")

# Distribute 5 ppl into 2 groups, but s.t. as few reunions as possible from
# groups of last round happen. This is handled as a MDGP instance.
last_round <- setNames(list(list(c("id001", "id003", "id005"), c("id002", "id04"))), Sys.Date() - 7)
rsocialroulette(frame, past_partitions=last_round, m=2, algorithm="mdgp", time_limit=1)
```

More complex partition algorithms, e.g., maximizing the distance in time since the people in the groups met the last time, are also available from the package. For more information see the [Getting started](https://hoehleatsu.github.io/socialroulette/articles/get-started.html) vignette of the package.

