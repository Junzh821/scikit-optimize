# Release history

## Version 0.5

High five!

## New features

* Single element dimension definition, which can be used to
fix the value of a dimension during optimization.
* `total_iterations` property of `BayesSearchCV` that
counts total iterations needed to explore all subspaces.
* Add iteration event handler for `BayesSearchCV`, useful
for early stopping inside `BayesSearchCV` search loop.
* added `utils.use_named_args` decorator to help with unpacking named dimensions
when calling an objective function.

### Bug fixes

* Removed redundant estimator fitting inside `BayesSearchCV`.
* Fixed the log10 transform for Real dimensions that would lead to values being
  out of bounds.

## Version 0.4

Go forth!

### New features

* Support early stopping of optimization loop.
* Benchmarking scripts to evaluate performance of different surrogate models.
* Support for parallel evaluations of the objective function via several
  constant liar stategies.
* BayesSearchCV as a drop in replacement for scikit-learn's GridSearchCV.
* New acquisition functions "EIps" and "PIps" that takes into account
  function compute time.

### Bug fixes

* Fixed inference of dimensions of type Real.

### API changes

* Change interface of GradientBoostingQuantileRegressor's predict method to
  match return type of other regressors
* Dimensions of type Real are now inclusive of upper bound.


## Version 0.3

Third time's a charm.

### New features

* Accuracy improvements of the optimization of the acquisition function
by pre-selecting good candidates as starting points when
using `acq_optimizer='lbfgs'`.
* Support a ask-and-tell interface. Check out the `Optimizer` class if you need
fine grained control over the iterations.
* Parallelize L-BFGS minimization runs over the acquisition function.
* Implement weighted hamming distance kernel for problems with only categorical dimensions.
* New acquisition function `gp_hedge` that probabilistically chooses one of `EI`, `PI`
or `LCB` at every iteration depending upon the cumulative gain.

### Bug fixes
* Warnings are now raised if a point is chosen as the candidate optimum multiple
times.
* Infinite gradients that were raised in the kernel gradient computation are
now fixed.
* Integer dimensions are now normalized to [0, 1] internally in `gp_minimize`.

### API Changes.
* The default `acq_optimizer` function has changed from `"auto"` to `"lbfgs"`
in `gp_minimize`.


## Version 0.2

### New features

* Speed improvements when using `gp_minimize` with `acq_optimizer='lbfgs'` and
`acq_optimizer='auto'` when all the search-space dimensions are Real.
* Persistence of minimization results using `skopt.dump` and `skopt.load`.
* Support for using arbitrary estimators that implement a
`return_std` argument in their `predict` method by means of `base_minimize` from `skopt.optimizer.`
* Support for tuning noise in `gp_minimize` using the `noise` argument.
* `TimerCallback` in `skopt.callbacks` to log the time between iterations of
the minimization loop.


## Version 0.1

First light!

### New features

* Bayesian optimization via `gp_minimize`.
* Tree-based sequential model-based optimization via `forest_minimize` and `gbrt_minimize`, with support for multi-threading.
* Support of LCB, EI and PI as acquisition functions.
* Plotting functions for inspecting convergence, evaluations and the objective function.
* API for specifying and sampling from a parameter space.


# Contributors

See `AUTHORS.md`.
