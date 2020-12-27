ML algorithm is algo that is able to learn from data. Ml algorithm gain experience E in task T by learning and 
achieves performance P.

#### The Performance Measure, P 
it is always specific to problem.quantitative measure to evaluate performance of an algorithm.we often use accuracy,
which is proportion of examples for which model produces correct output.equivalent information can also be obtain by 
measuring error rate, proportion of examples for which model produces an incorrect output.

#### Capacity, Overfitting abd Underfitting
ability to perform well on unobserved data by an algo. is known as generalization. generalization error makes difference
between optimization problem and ML problem. stastical learning theory gives insight about how to improve test error.
some of the key points are: examples in each dataset should be independent from each other, training and test set are 
identicaly distributed and both drawn from same probability distribution.because of taking samlpes from
distribution and then choose parameters to reduce training error, expected test error can be greater. our goal for training
any ML algo. is to -make training error small. -make gap between training and test error small.

this situation leads to under fitting and over fitting problems. underfitting occurs when model doesn't obtain sufficiently
low error on training set. overfitting occurs when gap between training set and test set is too large. and this behaviour
can be controlled by model's capacity. model's capacity is to fit wide variety of functions. model with low capacity can 
underfit and with high capacity can overfit.capacity can be controlld by choosing learning algorithms
hypothesis space, which is set of functions learning algo is allowed to selct as solution.
algorithm will generally perform best when there capacity is appropriate for complexity of problem. model's capacity 
should be decided by number of parameters model have, which depends on number of input features.VC dimention is wellknown 
method to quantify model's capacity.it is defined as largest value of m for which there exists training set of m different x
points that classifier can label.hence difference between training and generalization error grows when capacity grows but
shrinks when training set increases. learning algorithm's effective capacity can be less than representational capacity 
because of choice of optimization algorithm. ideal model is an oracle that simply knows the true probability distribution
of data. error made in predction by model is known as Bayes error.

#### The No Free Lunch Theorem
Inductive reasoning or infering general rules from limited set of examples is not logically valid. to logically infer rule
about every member, you must have information about every member. theorem states that averaged over all possible data-generating
distribution, every classification algo. has same error rate when classifying previously unobserved points. but if we make 
assumption about kinds of probability distribution we encounter, our learning algo. can perform better.

#### Regularization
from above theorem, we must design our algo. to perform specific task. when we build set of preferences
into algo. and when they aligned with problem, our algo. perform better. regualrizarion is another way
to form hypothesis space of model after capacity.

#### Hyperparameters and Validation Sets
Most machine learning algorithms have hyperparameters, settings that we canuse to control the algorithm’s behavior.
More frequently,the setting must be a hyperparameter because it is not appropriate to learn that hyperparameter on the 
training set. to avoid problem, we can use validation set which is composed of examples coming from the same 
distribution as the training set, can be used to estimate the generalization error of a learner, after the learning 
process has completed.

#### Cross-Validation
Procedures are based on the idea of repeating the training and testing computation on different randomly chosen subsets
or splits of the original dataset. The most common of these is the k-fold cross-validation procedure in which a partition 
of the dataset is formed by splitting it into k non overlapping subsets.

#### Estimators, Bias and Variance
Point estimation is the attempt to provide the single “best” prediction of some quantity of interest. While almost any 
function thus qualifies as an estimator, a good estimator is a function whose output is close to the true underlying θ 
that generated the training data. Since the data is drawn from a random process, any function of the data is random. 
Therefore estimate of parameter is a random variable.Point estimation can also refer to the estimation of the relationship 
between input and target variables.

Function Estimation: sometimes we try to predict y given data x, known as function estimation. Function estimation is
really just the same as estimating a parameter θ; the function estimator f is simply a point estimator in function space.

Bias of an estimator is defined as difference between expectation of the data and true underlying
value.

The variance of an estimator how much estimator will vary as function of data.The variance, or the standard error, 
of an estimator provides a measure of how we would expect the estimate we compute from data to vary as we independently 
resample the dataset from the underlying data-generating process. When we compute any statistic using a finite number of
samples, our estimate of the true underlying parameter is uncertain. 

Bias and variance measure two different sources of error in an estimator. Bias measures the expected deviation from the 
true value of the function or parameter.Variance on the other hand, provides a measure of the deviation from the 
expected estimator value that any particular sampling of the data is likely to cause. Desirable estimators are 
those with small MSE and these are estimators that manage to keep both their bias and variance somewhat in check.
When generalization error is measured by the MSE (where bias and variance are meaningful components of generalization error),
increasing capacity tends to increase variance and decrease bias.

#### Maximum Likelihood Estimation
Maximum Likelihood Estimation is the principle from which we can derive specific functions that are good estimators for 
different models instead of guessing. One way to interpret maximum likelihood estimation is to view it as minimizing the 
dissimilarity between the empirical distribution, defined by the training set and the model distribution, with the 
degree of dissimilarity between the two measured by the KL divergence. Minimizing this KL divergence corresponds exactly 
to minimizing the cross-entropy between the distributions which also known as negative log-likelihood of a Bernoulli or 
softmax distribution.

#### Maximum a Posteriori (MAP) Estimation
While the most principled approach is to make predictions using the full Bayesian posterior distribution over the parameter,
it is still often desirable to have a single point estimate bcz most operations involving the Bayesian posterior for most
interesting models are intractable, and a point estimate offers a tractable approximation.As with full Bayesian inference, 
MAP Bayesian inference has the advantage of leveraging information that is brought by the prior and cannot be found in 
the training data.
