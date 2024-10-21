# Simulating individual movement in fish

Data on the positions and movement statistics of 60 individual three-spined stickleback (*Gasterosteus aculeatus*) fish are available from the University of Lincoln Repository, [https://eprints.lincoln.ac.uk/id/eprint/55426/](https://repository.lincoln.ac.uk/ndownloader/files/43767666) (as an object in R data format, fishData.rds).

Load the object

```R
fishData <- readRDS(file.choose())
```

Look at its structure. It is a list of length 60 (i.e., it contains data for 60 fish)...

```R
length(fishData)
```

```
[1] 60
```

... and for each fish it contains the following elements (e.g., for fish 1)

```R
str(fishData[[1]])
```

```
List of 6
 $ smoothed.position:List of 3
  ..$ x: num [1:36000] 81.5 74.4 67.8 61.9 57.1 ...
  ..$ y: num [1:36000] 41.9 39 36.7 35.6 36 ...
  ..$ z: num [1:36000] 37.7 35.3 33.2 31.6 30.9 ...
 $ rho.s            : num 0.858
 $ shape            : num 2.7
 $ rate             : num 0.775
 $ kappa            :List of 2
  ..$ k: num 2.83
  ..$ d: num 1.98
 $ beta             :List of 2
  ..$ k: num 0.452
  ..$ d: num 2.26
```

These elements are as follows:
* `smoothed.position`: the [x,y,z] positions of the fish after smoothing.
* `rho.s`: the Spearman's rank correlation coefficient describing step length autocorrelation at lag 1.
* `shape`, `rate`: the parameters of the best-fitting gamma distribution for step length.
* `kappa`, `beta`: the coefficient (`k`) and exponent (`d`) of the power-law relationship between step length and the concentration (κ) and ovalness (β) parameters of the best-fitting Kent distributions.
 
### Example usage

```R
plot(fishData[[1]]$smoothed.position$x[1:360], fishData[[1]]$smoothed.position$y[1:360], xlab="x (mm)", ylab="y (mm)", asp=1)
```
